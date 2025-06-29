# Systems Mapping Sheets - Philip Garnett

Presented here are the structured spreadsheets that can either be used alone to capture network structure, or then combined with the software tools (link to repo to follow) to produce a variety of network outputs (e.g. Neo4J databases, GraphViz files, etc). These sheets have been developed and refined over a number of projects ([Algorithmic Indexing](https://algorithmicindexing.net), [MapUKHE](https://mapukhe.net/), [ActEarly](https://actearly.org.uk/)) to support gathering network/graph data of relationships for systems mapping or complex network analysis. They are a convenient and structured way of collecting and storing systems mapping data, and as their structure is fairly intuitive, importing them into a variety of different software packages is straightforward.

The spreadsheets have two versions, one for the collection of information about nodes and the other for the collection of relationship data. They are separated this way as it allows for easier collection of attributes (both node and edge attributes) and one-to-many relationships (where one node connects to many other nodes).

It should be noted that any attribute containing the string 'date' within it will be treated as a date object and therefore should follow the date pattern YYYY-MM-DD. The program also expects that the first line of the file is the header information; do not deviate from the header column names.

## The nodes sheet
As a minimum, nodes must have a type and one attribute which uniquely identifies that node, they can then have any number of further attributes. The structure of the nodes sheet can be seen in file nodes_sheet.png, and a CSV/xlsx version is available as well.

![Demo of the nodes sheet](nodes_sheet.png)

As shown in the image, the nodes sheet is relatively simple. The first column records the node type (we will add notes on how to choose types etc later), the second column records the label of the first attribute, and the third column the value of that attribute. The rest of the columns record pairs of attributes, label name and value, and can be expanded to accommodate any number of attributes. One attribute needs to uniquely identify the node, and we recommend that this be recorded first as in many cases that might be the only attribute. Think of this as the unique ID of the node; it can be a string label (but make sure you are perfectly consistent) or a number etc. It should be noted that not all output formats support attributes on nodes in the same way.

## The relationship sheet
The relationship sheet is similar but slightly more complicated, see edges_sheet.png and the CSV/xlsx files. Relationships at a minimum need to have the type of the two nodes defined (node_type_1 and node_type_2), a match key for each node (the attribute label of the unique attribute of the nodes you are matching on, match_key_1 and match_key_2), and the corresponding match id (the value associated with the label of the unique attribute of the nodes, match_id_1 and match_id_2), and the relationship type (rel_type). These pieces of information uniquely identify the two nodes included in the relationship, and the type of relationship to be formed, and are stored first in the table. All further attributes are handled in the same way as for nodes, pairs of attribute labels and values and you can have as many as you want. It should be noted that not all output formats support attributes on relationships in the same way.

![Demo of the relationships/edges sheet](edges_sheet.png)
As shown in edges_sheet.png, for the relationships the required information to form the relationship is stored in the first columns of the file. Starting with the type of the nodes in the relationship, then the unique identifiers, and then the relationship type. Further attributes follow afterwards.

The 'match keys' are the attributes of the node that you are going to use to identify them, and the 'match id' is the expected value for that attribute that is used to search for the node to create the relationship. The naming of the id is important; it needs to be exactly the same (and unique to one node) as the value in the node database otherwise no relationship will be formed.
