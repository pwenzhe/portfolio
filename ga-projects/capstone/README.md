# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Donor Leads through Network

> SG-DSI-41: Poon Wenzhe

---

> __Github Portfolio Notice:__ This folder excludes all obtained data and the web scraping code. Please contact via email if you wish to know more about this project.

### Introduction

The donor landscape in Singapore continues to evolve. Income through fundraising and donations is a common challenge for charities in Singapore, especially for smaller charities.

This is a capstone project that explores using network analysis for the problem statement.

### Problem Statement

To recommend new donor leads for fundraising through network analysis of donors and charities.

### Organization

The notebooks in the `code` folder is ordered accordingly:

1. Web Scraping
2. EDA and Data Prep
3. Network Prep and Exploration
4. Network Community Detection
5. Recommender System

### Data and Assumptions

Data is collected via Selenium web scraping of the Charity Portal to gather information about Charities as well as members related to each charity, such as Board Members. This dataset is to simulate an early stage data collection that relates donors to charities.

Features of the charities were extracted and engineered to capture key areas of interests a donor may have to a charity, such as the charity's activities, classification, and Institution of Public Character (IPC) status.

### Method

This project applies various concepts to recommend donors. A major component and starting point is the community detection which clusters nodes of the network. This is done in an unsupervised manner as the dataset is large and no ground truth is available, but nevertheless a useful method to identify similar nodes based on the network alone.The metric used for evaluating the quality community detection is modularity. Network graphs are also visually inspected.

This project also uses other concepts to assess the suitability to recommend donors to a given target charity by:

1. Inferring interest of the donor through similarity of charities connected to the donor
2. Distance of the donor to the target charity
3. The centrality of donors in a subgraph network of the target charity

Ultimately, the project delivers a scoring recommendation of new donor leads for a given charity based on the concepts applied.

### Findings

By the end of the project, the following methods were chosen after exploration with other methods:

1. Commmunity Detection: Ego-Splitting Framework
2. Similarity: Jaccard Similarity
3. Centrality: Eigenvector Centrality

The Ego-Splitting community detection method had high modularity metric indicating good quality of communities being created, and visual inspection shows communities made by this method fit better for this network. Jaccard similarity and eigenvector centrality were chosen based on the problem statement.

### Demo (Streamlit)
A demo is available for this project. This demo allows generation of recommended donor leads for any available charity. Additional libraries are required:

- `streamlit`
- `karateclub`

#### Required Files
The following files are required for this demo:

- `data\charities.csv`: data on charities
- `json\graph.json`: the full graph data stored in json

#### Running the Demo
1) Use a terminal such as command prompt or Anaconda prompt depending on the installation path of Python, change the directory to point the the `demo` folder
2) Run the line on the terminal `streamlit run demo.py`
3) When the streamlit demo is successfully running, the terminal will display the Local URL, which shows the localhost port used on the machine, and the Network URL

To allow other machines to connect to the Network URL, go to your machine's Firewall settings and allow `python.exe` to access networks. The other machines should be connected to the same network as the machine you are using to host the streamlit demo.

### Conclusion

1. Unsupervised ommunity detection is possible on the network with high modularity.
2. A recommendation system can be made with a mixture of network based analysis.
3. An interested party can obtain a list of recommended donors for a given charity as well as the supporting scores behind the recommendation.


### Future Work
For future work and to further improve on this project:
1. Use a network with person-person connections
2. Enhance using the centrality measure with a weighted network based on the current recommendation score
3. Propagate information from charities to donors for item-user collaborative filtering, and explore the use of clustering on persons when features are available
4. Explore other metrics such as Jaccard Distance
