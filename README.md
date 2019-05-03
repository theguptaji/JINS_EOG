# JINS_EOG


The following repository contains Data collected with JINS MEME device on 21 pairs(42 people).

## data/raw contains the raw csv files recorded at 100hz, which contains 10 different datapoints (3 EOG, 3 GYRO, 3 ACC, Timestamp). 

All folders ranging from 1- 21 represents pairs of two people. Inside each folder contain two different folders named 'L' and 'R' which are notations weather person was sitting on left or right. and these contains there respective CSV files.

but they need to be synchronised. 
Syncronisation can be done with the help of UNIX TIMESTAMPS,
and after that the two sets of 300 sec recordings(30000 values) can be extracted by locating the 'x' in '//Artifact' column.
There is a possibility that not both the files have x, so please use the timestamp corresponding to any 'x' for extracting the data


## data/pkl contains the processed EOG data, which does not need any sort of synchronisation and can be used directly.

the format of the files are .pkl and can be opened with pandas python.
a typical files looks like this:-
```
A - D - Pair 21 - CW morlet Coherence on EOG_V.pkl
B - D - Pair 21 - CW morlet Coherence on EOG_V.pkl
```
Here A means when people are sitting facing each other, while in B they were sitting back to back.
(D means the raw data)

after loading the file like this:-
```
data = pd.read_pickle( 'A - D - Pair 21 - CW morlet Coherence on EOG_V.pkl' )
```
EOG's can be accessed with 
```
D['A']['L']   - face to face for left person
D['A']['R']   - face to face for Right person
D['B']['L']   - back to back for left person
D['B']['R']   - back to back for Right person
```


