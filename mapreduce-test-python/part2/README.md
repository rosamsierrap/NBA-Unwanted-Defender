# NBA Shot data analysis (Part 2)

Q1: looks into finding the "most unwanted defender". Meaning: the player causing the lowest shot success rate when faced by another player.

For this particular case we needed a single Mapper and a single Reduce. In the mapping process we extracted player information from the input csv, did some simple data cleaning and created KVPs with the form `((shooter, defender), (made))`.
The reducing process creates a dictionary and checks the lowest rate of made shots based on the key (shooter,defender)

## Getting Started

Proceed to clone the repository into the Cloud cluster.

`git clone https://github.com/rosamsierrap/NBA-Unwanted-Defender.git `

## Data

The data used in this analysis was obtained from Kaggle, which can be accessed here: https://www.kaggle.com/datasets/dansbecker/nba-shot-logs

## Usage

To run this code you need a functional HDFS system running, for our experiments a 3 node cluster hosted on Google Cloud was the way to go. Two worker nodes and one manager orchestrating.
The driver code is stored in the files `test.sh` for `Q1` and they will run the mappers/reducers to answer all the questions. Make sure to double check the appropiate location for the data csv, it can be found
inside of the driver code where there's a copyFromLocal statement `/usr/local/hadoop/bin/hdfs dfs -copyFromLocal ../../../mapreduce-test-data/shot_logs.csv /part2/input/`. 
This route is expected to be different depending on each system file distribution. 

## Findings

- Q1. The player pairs with the highest fear score are Dennis Schroder vs Jerryd Bayless (203471-201573) and Norris Cole vs Goran Dragic (202708-201609), with a score of 0.00% in both cases. This means that out of 10 shots made 0 were successful for these two pairs, making them the most unwanted defenders for their respective shooters, being Schroder and Dragic the defenders


## Conclusion 

Through the use of this MapReduce framework we are able to analyze dense NBA data and draw several conclusions about how players perform. 

