# 1001 Albums Project Final Report

## Project Summary
*1001 Albums You Must Hear Before You Die* is a book by Robert Dimery that takes some of the most influential and/or best albums released since the 1950's and makes a case for why they are important, using the reviews of music critics. I created a database with all the artists and albums on the list and added all the songs listed as a part of those albums on musicBrainz API. I wasn't able to complete the vectorization portion because I wasn't able to access song data like BPM and key without spending a ridiculous amount of money, but I plan to make a smaller version later and calculate that info from a few albums' worth of MP3 files.


### ERD
[Initial ERD](static/initial_ERD.jpg)

I completed most of the ERD. I wasn't able to add all of the attributes of each song since the Spotify API I planned on using doesn't offer BPM and similar info anymore, and getting that info with librosa would require me to buy MP3 files for all the albums, which is impractical. 

### System Design
[Initial System Design](static/initial_program_design.jpg)

Although I was only able to complete the DB for this project, it is still the model I am working with. I intend to fully implement this model with a smaller dataset later.


### Demo Video
I don't have a working prototype, but here is a gif of me querying my database in neo4j.

![Querying DB](static/neo4j_DB_demonstration.gif)


### What Did I Learn
* **Time spent planning in advance is well worth it.** I spent a couple of hours planning out my ERD and project design, but I wished I had looked further into Spotify API and librosa before starting my project. If I had done that, I would have reconsidered the scope of my project. 
*  **Working with APIs.** I hadn't worked with a lot of external APIs before, so it was fun to work with MusicBrainz. I learned about including headers in my requests and about requests per second limits.
*  **Neo4j.** I used Neo4j for this project since I wanted to learn more about graph DBs. I learned about the syntax, merging, deleting nodes, adding attributes to nodes, creating a Neo4j instance, and connecting to that instance. I think that it is a bit expensive, so I probably won't use it for larger datasets in the future.
*  **Consistency and Formatting with Input Files.** In order to get songs from each album, I read from a CSV file with all the albums and their artists. This worked fine for about 850 of the albums, but I ran into problems with some of the entries because of some of the spellings. MusicBrainz wouldn't return results unless the artist and album names were pretty close to what it had listed. This caused problems when albums or artists used special characters, added the word "The", or when apostrophes were replaced with underscores in the CSV. It ended up being enough of an issue that I had to retrieve about 100 album Ids by hand from MusicBrainz. I don't know that there was a better way I could fix it, but in the future, I would want my inputs to match the API. 

### AI Usage
My project does not integrate AI. However, I used AI for several parts of the project. I used Claude to find external services I could use for getting music info. That is where I got MusicBrainz, SpotifyAPI, and librosa from. I used Claude to help connect to MusicBrainz API, to write quick queries within Neo4j to check for issues in my database, and to write some of the queries used in building the database. I also used Claude to help with debugging.


### Why This Project Is Interesting To Me
I really enjoy music and am interested to learn more about it. When we went over vectorization in class, I was really interested in it because I started to understand how recommendations actually work, so I decided that I wanted to use it in my project. A music recommendation service seemed obvious because it would allow me to learn more about the musical cannon as I coded and learned more about vectorization. It is also the sort of service I would like to use myself, so I was interested as a consumer as well.


When I was working on the database, I learned a lot about using APIs and existing data. I learned that spelling and formatting choices can really matter when using API search capabilities. This was the primary source of problems I had while coding. I also learned how to read responses from the API and to be mindful of exactly what data I am adding to the DB. For example, I found that I was accidentally adding songs for every medium of every album, which meant that I was adding duplicates of most songs. These are considerations that I will keep in mind the next time I request a list of data from an API. All in all, I had a good time working on this project and am excited to carry it out on a smaller scale.

## Explanation of Strategies
I didn't get far enough to worry about a failover strategy, scaling, performance, authentication, etc.