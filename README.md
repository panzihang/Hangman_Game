# Hangman Game
Hangman game is a paper and pencil guessing game for two or more players. One player thinks of a word,  and the other(s) tries to guess it by suggesting letters within a certain number of wrong guesses. <br>
https://en.wikipedia.org/wiki/Hangman_(game) <br>
### Game Overview:
The word to guess is represented by a row of dashes, representing each letter of the word. <br>
If the guessing player suggests a letter which occurs in the word, the other player writes it in all its correct positions. The guessing player then continue guessing the next letter. (Succesful guess does not count toward total chances.) <br>
If the suggested letter does not occur in the word, the other player draws one element of a hanged man stick figure as a tally mark. (Or say, losing one chances of guessing.) <br>
If the guessing player loses all chances, which is usually 6, representing head, body, two arms and two legs, he/she is then 'hanged' and loses the game. <br>
<img src="Hangman_game.jpg" width=180>

### An example:
Secret word: Hangman,  <br>
Total chance: 6.

1st guess: e: _ _ _ _ _ _ _; Chances left: 5; <br>
2st guess: a: _ a _ _ _ a _; Chances left: 5; <br>
3st guess: n: _ a n _ _ a n; Chances left: 5; <br>
4st guess: t: _ a n _ _ a n; Chances left: 4; <br>
5st guess: e: _ a n _ _ a n; Chances left: 3; <br>
6st guess: g: _ a n g _ a n; Chances left: 3; <br>
7st guess: h: h a n g _ a n; Chances left: 3; <br>
8st guess: m: h a n g m a n; Chances left: 3; <br>
**Then this is a success!**

## My work
Developed the game framework in the Jupyter Notebook. <br>
It includes:
* Raw training and testing words.
* Functions to generate a secret word, start the game and keep track of it.
* Functions applying ***my strategy*** to guess the word.

## My strategy
A data scientist may find this NLP problem well-suited for Machine Learning and Nerual Networks. *However, my strategy is inspired by what human really think when guessing an English word - **we focus on substrings**.*

English words usually consist of common substrings, such as '-tion', '-ness', 'pre-', '-it-', 're-', '-en-'...... <br>
I first abstract these substrings from the training corpus, and count their occurrencies, then use these substrings to match the substring in the masked secret word. <br>
For example, the current masked word is: 'l e a r _ i _ g', a very common substring 'ing' matches with the current mask 'i _ g', showing that this masked letter is very likely to be an 'n'. <br>
I apply this method to each position, calculating the possibilities of it being each letter by matching substrings to it and its neighbours. Then I guess the letter that has max possibility in each round.<br>

This strategy reaches 56% accuracy guessing the word from both train and test corpus. It is a good result since there are many English words with unusual construction and letters. It also out-performs the Neural Networks that others developed, in both running time and accuracy.

Please go into the notebook to see detailed examples of game playing and strategies. <br>
*Don't forget to try providing a secret by yourself!*