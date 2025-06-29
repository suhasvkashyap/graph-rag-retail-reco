# Graph-RAG Personalized Retail Recommendation System

🛒 **A complete implementation of Graph-RAG for intelligent, context-aware retail product recommendations**

![Graph-RAG Architecture](https://img.shields.io/badge/Graph--RAG-Retail%20Demo-blue) ![IBM watsonx.ai](https://img.shields.io/badge/IBM-watsonx.ai-blue) ![LangChain](https://img.shields.io/badge/LangChain-Framework-orange) ![NetworkX](https://img.shields.io/badge/NetworkX-Knowledge%20Graph-purple)

## 🎯 What This Project Solves

Traditional recommendation systems treat user interactions in isolation, missing the rich contextual relationships that drive real purchasing decisions. This Graph-RAG implementation addresses key limitations:

### Problems with Traditional RAG:
- **❌ Isolated recommendations**: "You bought earbuds? Here are more earbuds"
- **❌ No user context**: Ignores purchase history and preferences
- **❌ Missing relationships**: Can't connect complementary products
- **❌ Generic suggestions**: Same recommendations for different user types

### How Graph-RAG Improves This:
- **✅ Contextual understanding**: "Sarah loves sustainability" → eco-friendly products across all categories
- **✅ Relationship awareness**: Wireless earbuds → phone cases, power banks, cleaning kits
- **✅ User profiling**: Sports enthusiasts get performance-focused recommendations
- **✅ Multi-hop reasoning**: Connects users → products → features → reviews for richer context

## 🏗️ System Architecture

```
📊 Data Sources → 🕸️ Knowledge Graph → 🎯 Graph-RAG System
     ↓                    ↓                    ↓
🗃️ CSV Files        NetworkX Graph      🤖 IBM watsonx.ai
                         ↓                    ↓
              🗃️ Vector Store ←→ 📱 Personalized Recommendations
```

## 🌟 Key Features

- **🤖 IBM watsonx.ai Integration**: Llama-3-3-70B LLM + Granite embeddings
- **🕸️ Knowledge Graph**: NetworkX-based graph with users, products, features, and reviews
- **🔗 Graph-RAG Pipeline**: LangChain framework for retrieval and generation
- **🎨 Beautiful Visualizations**: Interactive network graphs and recommendation displays
- **📊 Multiple Recommendation Types**:
  - 🏃 Sports & Athletic Products
  - 🌱 Sustainability & Eco-friendly Items  
  - 🎧 Complementary Products
- **📈 System Analytics**: Complete graph analysis and metrics

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- IBM watsonx.ai account (optional - works with fallback responses)

### Installation

1. **Clone the repository**:
```bash
git clone https://github.com/yourusername/graph-rag-retail-demo.git
cd graph-rag-retail-demo
```

2. **Install dependencies**:
```bash
pip install pandas numpy networkx matplotlib seaborn python-dotenv
pip install langchain-community langgraph langchain-huggingface 
pip install sentence-transformers langchain-ibm ibm-watsonx-ai
```

3. **Set up environment variables** (optional):
Create a `.env` file in the project root:
```env
WATSONX_API_KEY=your_api_key_here
WATSONX_PROJECT_ID=your_project_id_here
WATSONX_URL=https://us-south.ml.cloud.ibm.com
HF_TOKEN=your_huggingface_token_here
```

4. **Run the notebook**:
```bash
jupyter notebook graph_rag_retail_demo_working.ipynb
```

## 📖 How to Use

### 1. **Data Generation**
The notebook automatically generates realistic synthetic retail data:
- Product features (50 products across 10 categories)
- User purchase and browsing history (20 users)
- Product reviews with ratings
- User profiles with names and preferences

### 2. **Knowledge Graph Construction**
- Creates a heterogeneous graph with 160+ nodes
- Establishes relationships: purchased, browsed, has_feature, wrote_review
- Builds rich context for recommendation generation

### 3. **AI Model Setup**
- **With watsonx.ai**: Uses real Llama-3-3-70B for generation + Granite embeddings
- **Without watsonx.ai**: Intelligent fallback responses for demonstration

### 4. **Generate Recommendations**
Run the example cells to see three recommendation types:

```python
# Sustainability-focused
query1 = "Sarah Martinez loves sustainability—suggest eco-friendly items."
result1 = rag_chain.generate_recommendation(query1, user_id=3)
display_sustainability_recommendations(result1, product_features_df)

# Sports & Performance  
query2 = "John Anderson browsed sports gear—recommend performance products."
result2 = rag_chain.generate_recommendation(query2, user_id=7)
display_recommendation_table(result2, product_features_df)

# Complementary Products
query3 = "Ashley Williams highly rated wireless earbuds—what complementary products?"
result3 = rag_chain.generate_recommendation(query3, user_id=12)
display_complementary_recommendations(result3, product_features_df)
```

### 5. **Visualize the Graph**
The final cell creates beautiful network visualizations showing:
- Complete knowledge graph structure
- User-product interaction patterns
- Node and edge distributions
- Graph analytics and metrics

## 🎨 Output Examples

### Sustainability Recommendations
```
🌱 Top 5 Sustainability & Eco-Friendly Recommendations
🎯 Query: Sarah Martinez loves sustainability—suggest eco-friendly items.
👤 User: Sarah Martinez

🌿 Sustainability Profile
🛒 Past Eco-Friendly Purchases: Premium Eco-friendly Green Electronics, Sustainable Fashion...

🏆 Top 5 Sustainability & Eco-Friendly Recommendations
① 🌱 Eco-Friendly Electronics - Energy-efficient devices with ENERGY STAR certification...
② 👕 Sustainable Fashion & Clothing - Organic cotton and recycled materials...
③ ☀️ Solar-Powered Home Gadgets - Renewable energy devices...
④ 🪑 Recycled Materials Furniture - Stylish furnishings from reclaimed materials...
⑤ 🧴 Biodegradable Personal Care - Natural products with minimal packaging...
```

## 🔧 Configuration Options

### Customize User Profiles
Modify the `USER_NAMES` dictionary to add your own users:
```python
USER_NAMES = {
    1: "Your Name", 
    2: "Another User",
    # ... add more users
}
```

### Adjust Recommendation Types
Edit the fallback recommendation functions to customize:
- Product categories
- Feature preferences  
- Recommendation logic

### Modify Graph Structure
Change the synthetic data generation to:
- Add more product categories
- Increase user/product counts
- Include additional features

## 📊 Technical Details

### Architecture Components
- **Data Layer**: CSV files with retail transaction data
- **Graph Layer**: NetworkX knowledge graph with 4 node types
- **AI Layer**: IBM watsonx.ai for embeddings and text generation  
- **RAG Layer**: LangChain framework for retrieval and generation
- **Application Layer**: Jupyter notebook with interactive displays

### Performance Metrics
- **Graph Density**: ~6% (optimal for recommendation graphs)
- **Node Distribution**: Users (20), Products (50), Features (6), Reviews (84+)
- **Edge Types**: 5 different relationship types
- **Response Time**: <3 seconds for most recommendations

## 🤝 Contributing

We welcome contributions! Please feel free to:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit changes**: `git commit -m 'Add amazing feature'`
4. **Push to branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Areas for Contribution
- Additional recommendation algorithms
- New visualization types
- Performance optimizations
- Additional AI model integrations
- Extended synthetic data generation

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **IBM watsonx.ai** for providing powerful LLM and embedding capabilities
- **LangChain** for the excellent RAG framework
- **NetworkX** for robust graph manipulation tools
- **Hugging Face** for open-source embedding models

## 📧 Support

If you encounter any issues or have questions:

1. **Check the Issues**: Look through existing GitHub issues
2. **Create New Issue**: Describe your problem with steps to reproduce
3. **Discussions**: Use GitHub Discussions for general questions

## 🎯 Next Steps

After running this demo, consider:

- **Scaling**: Implement with real retail data
- **Production**: Deploy using cloud infrastructure  
- **Integration**: Connect to existing e-commerce platforms
- **Enhancement**: Add real-time learning capabilities
- **Expansion**: Include more sophisticated user modeling

---

**⭐ If this project helps you, please give it a star! It helps others discover this work.**

*Built with ❤️ for the retail AI community*