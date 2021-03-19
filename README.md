# Country Music Lyrics Generator


## Problem Statement

Using a Recurrent Neural Network, could a model generate lyrics to our next Country music hit? 

## Goal

A neural network that will generate song lyrics based off training on current released country lyrics and predicting a new song that will hopefully become the next number one hit. Will there be trends in the data that are worth addressing? Can the RNN predict whole coherent words? If so, would coherent sentences be too much to ask for?

## DATA

[Lyrics Scraped Data](https://raw.githubusercontent.com/samnangpeou/CAPSTONE_GA/main/data/country_lyrics.csv "Lyrics Scraped from Genius API")
[Cleaned Data](https://https://raw.githubusercontent.com/samnangpeou/CAPSTONE_GA/main/data/data_cleaned.csv "Cleaned Data")


## Column Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|lyrics|object|lyrics/data_cleaned|Lyrics scraped from Genius API.|
|url|object|lyrics/data_cleaned|URL lyrics were scraped from.|
|lyrics_length|int|lyrics/data_cleaned|Length of lyrics in characters.|
|lyrics_word_count|int|lyrics/data_cleaned|Word count for lyrics.|


![alt text](https://github.com/samnangpeou/CAPSTONE_GA/blob/main/img/guitar.png?raw=true)


## Research:

Genius is a social media website that lets users create annotations on song lyrics, news stories, etc. The Genius API allows you to have access to the information on that website including the lyrics. Used the API for data retrieval and scraped about 5,500 songs and appended them to a single CSV. The data consists of 74 different artists, 5,500 songs, a different amount of songs per Artist because not all artists have a ton of songs. Some have a lot, some have just 10. Artists like Luke Combs, Reba McEntire, Kenny Chesney, Alan Jackson, George Strait, Taylor Swift, etc.

IMG HERE

## Modeling:

Splitting the data into sequences of 80 characters, the training data is everything but the last character in the sequence and the target data is everything else but the first character. The model would be predicting the very last character in the sequence. I trained 2 RNN's with a GRU and LSTM layer and pinned them against eachother but only training them for shorter periods.

IMG HERE

The GRU Model outperformed the LSTM in earlier epochs and trained a sufficient model.

# Sample Lyrics:

Since the model predicts on the next character following a sequence, once you give the model a constant, it will predict the next character in a loop depending on how long you want the loop to be. Here are some with 120 characters following constants: 'Beer ', 'LOL ', and 'General Assembly '.

IMG HERE

Pretty solid if you ask me.


## Conclusion and Recommendations:

So no, this is not a number one hit. The snippets barely make sense. Although, with limited data, I was able to train a model that spat out words. Words in sequences that somewhat make sentences. That's a win. I did train an LSTM model and the loss drops a lot lower than the GRU model in later epochs. Extracting predictions from that LSTM model became a bit of a pain but in future iterations I'd like to revisit that issue and correct it to see how well an LSTM can predict lyrics.