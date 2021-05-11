# -hamgman-the-psychic-winner
# This game is in Python
import random
from words import words
import string

def get_valid_word(words):
    word = random.choice(words)
    #Randomly Chooses something from the list
    while '-' in word or ' ' in word :
      word = random.choice(words)
    
    return word.upper()


def hangman():
  word = get_valid_word(words)
  word_letters = set(word) 
  #Guess the letters in the word

  alphabet = set(string.ascii_uppercase)
  used_letters = set()
  lives = 6
  #What the User have Guessed 
  while len(word_letters) > 0 and lives > 0:
    #Letters used
    # ' '.join(['a', 'b', 'cd']) --> ' a b cd '
    print('You have ', lives ,'lives left and You have used these letters : ' , '  '.join(used_letters))

    #What current word is (ie W - R D )
    word_list = [letter if letter in used_letters else '-' for letter in word]
    print('Current Words : ',' '.join(word_list))
    user_letter = input('Guess a Letter :').upper()
    if user_letter in alphabet - used_letters :
        used_letters.add(user_letter)
        if user_letter in word_letters :
          word_letters.remove(user_letter)
        
        else:
          lives = lives - 1
          #Takes away a life if wrong 
          print('Letter is not in word. ')

    elif user_letter in used_letters:
     print('You have already guessed that word . Please try again')
  
    else:
    
     print('Invalid Character , Please Try Again . ')

  if lives == 0 :
    print('Sorry But You Died!!!, this word was', word)
  else:
    print('You guessed the Correct word', word) 

hangman()




  



  

