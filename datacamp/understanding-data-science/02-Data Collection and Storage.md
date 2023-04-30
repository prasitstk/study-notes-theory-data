# 02-Data Collection and Storage

## Data sources

### Sources of Data

**Company data**

- Collected by companies
- Helps them make data-driven decistions

**Open data**

- Free, open data sources
- Can be used, shared, and built-on by anyone

Note that sometimes companies share parts of their data with a wider public as well.

### Company data

- Web events
  - When you visit a web page or click on a link, usually this information is tracked by companies in order to calculate conversion rates or monitor the popularity of different pieces of content. 
- Survey data
  - Data can also be collected by asking people for their opinions in surveys. This can be, for example: 
    - a face-to-face interview, 
    - online questionnaire, or 
    - a focus group.
- Customer data
- Logistics data
- Financial transactions

### Open data

There are multiple ways to access open data. Two of them are: 

- APIs and 
- public records.

### Open data :: Public data APIs

API = Application Programming Interface. 

It's an easy way of requesting data from a third party over the internet. 

Some noteable APIs include Twitter, Wikipedia, Yahoo! Finance, and Google Maps, but there are many, many more.

### Open data :: Public records

Public records can be collected and shared by:

- International organizations 
  - like the World Bank, the UN, or the WTO, 
- National statistical offices
  - who use census and survey data
- Government agencies
  - who make information about for example the weather, environment or population publicly available. 

For example:

- In the US, **data.gov** has health, education, and commerce data available for free download. 
- In the EU, **data.europa.eu** has similar data.

---

## Data types

Important to care about the data types when:

- storing data
- visualize/analyze data

### Quantitative and Qualitative data

There are two general types of data: 

**Quantitative data**

- can be expressed using numbers
- can be counted, measured
- Ex. the fridge is 60 inches tall, has two apples in it, and costs 1000 dollars

**Qualitative data**

- descriptive and conceptual
- can be observed but not measured
- Ex. the fridge is red, was built in Italy, and might need to be cleaned out because it smells like fish.

### Other types

Other than the traditional quantitative and qualitative data, there are many other data types that are becoming more and more important. There is:

- Image data
  - Digital images are everywhere. An image is made up of pixels. These pixels contain information about color and intensity. Typically, the pixels are stored in computer memory. 

- Text data
  - Emails, documents, reviews, social media posts, and so on. As you can imagine, text data can be found in many places. This data can be stored and analyzed to find relevant insights. 
  - Ex. a restaurant review

- Geospatial data
  - Geospatial data are data with location information. Many different types of information can be captured using geospatial data.
  - Ex. For a specific region we can keep track of where the roads, the buildings, and vegetation are. 

- Network data
  - Network data consists of the people or things in a network, depicted by circles on the slide, and the relationships between them, depicted by lines on the slide. 
  - Ex. a social network. You can easily see who knows whom.

- and many more...

Note that these other data types aren't mutually exclusive with **quantitative and qualitative data**. 
Meaning often these other data types are a special **mix of quantitative and qualitative data**.

---

## Data storage and retrieval

### Things to consider when storing data

When storing data there are multiple things to take into consideration:

- Location:  where we want to store the data
- Data type: what kind of data we are storing
- Retrival: how we can retrieve our data from storage

### Location

**Parallel storage solutions**

Data science projects could require large amounts of data. At this point the data probably can't be stored on a single computer anymore. 

In order to make sure that all data is saved and easy to access, it is stored across many different computers. 

Large companies often have their own set of storage computers, called a “cluster” or a “server”, on premises.

**The cloud**

Alternatively, you could pay another company to store data for you. This is referred to as “cloud storage”. 

Common cloud storage providers include Microsoft Azure, Amazon Web Services, or AWS, and Google Cloud. 

### Types of data storage

Different types of data require different storage solutions. 

**Unstructured**

- email
- text
- video
- audio files
- web pages
- social media messages

This type of data is often stored in a type of database called a **Document Database**.

**Tabular**

Data can be expressed as tables of information.

A database that stores information in tables is called a **Relational Database**.

### Retrieval: Data querying

Once data has been stored in a **Document Database** or a **Relational Database**, we’ll need to access it. 

At a basic level, we’ll want to be able to request a specific piece of data, such as “All of the images that were created on March 3rd” or “All of the customer addresses in Montana”. 

In addition, we might even want to do some analysis, such as summing, counting, or averaging data.

Each type of database has its own query language:

- **Document Databases** -> use **NoSQL** = “Not only SQL”
- **Relational Databases** -> use **SQL** = “Structured Query Language”

### Putting it all together

Steps to decide about storing your data:

**Location**: Decide between

- On-premises cluster
- Cloud provider: Azure, AWS, Google Cloud

**Data type**: Decide type of data storage based on data types

- **Unstructured** -> **Document Databases**
- **Tabular** -> **Relational Databases**

**Query language**

- **Document Databases** -> **NoSQL**
- **Relational Databases** -> **SQL**

---

## Data Pipelines

Data engineers work to **collect and store data**, 
so that others, like analysts and data scientists can access data for their work, 
whether it's for visualization or building machine learning models.

### Problem :: How do we scale?

**Collect data from more than one data sources**

- Public records
- APIs
- Databases

**Data sources have different data types**

- Unstructured data
- Tabular data
- Real-time streaming data like tweet

This makes storing this incoming data **complicated**. 
Because as a data engineer, you want to make sure data is **organized** and **easy to access**.

### Solution :: Data pipeline

A **data pipeline** moves data into **defined stages**.

- for example, from data ingestion through an API to loading data into a database. 

A key feature is the data pipeline **automate this movement**. 

- Data is constantly coming in and it would be tedious to ask a data engineer to manually run programs to collect and store data. 
- Instead a data engineer:
  - *schedules tasks* whether it's hourly, daily, or 
  - tasks can be *triggered by an event* 
- Because of this automation, data pipelines need to be **monitored**. 
  - Luckily, **alerts** can be generated automatically
    - for example, when 95% of storage capacity has been reach or if an API is responding with an error. 

Data pipelines aren't necessary for all data science projects, but they are when **working with a lot of data from different sources**. 

There isn't a set way to make a pipeline
- pipelines are highly customized depending on your data, storage options, and ultimate usage of the data. 

### ETL

**ETL**, which stands for **extract, transform, and load**, is a popular **framework for data pipelines**.

**Extract**

First, we begin with **extracting all the data from the data sources we listed**, whether it's an API or setting up an IoT device.

Notice that the different frequencies and different structures of data sources makes us realize that **storing the raw data as is won't work**, so we need to **transform** them.

**Transform**

With all the data coming in, how do we keep it **organized** and **easy to use**? Here we do this for example:

- **Joining** data from different sources into **one dataset**
- **Converting** the incoming data's structure to fit **a database's schema**
  - A database's schema informs us how data must be structured before loading it in.
- **Removing** irrelevant data

Note that **Analytical tasks** like **Data preparation** and **exploration** does not occur at this stage

**Load**

Finally, we **load the data into storage** so that it can be used for visualization and analysis.

**Bring it all together :: Automation**

Once we've set up all those steps, we automate them. 

There are tools that specialized to do this, the most popular is called **Airflow**.

---
