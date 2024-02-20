<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Black Color Detection & Guessing Game</title>
<style>
  body {
    background-color: black;
    color: white;
    font-family: Arial, sans-serif;
  }
</style>
</head>
<body>
<h1>Black Color Detection & Guessing Game</h1>
<p id="detectionResult"></p>
<p>Try to guess the number between 1 and 100:</p>
<input type="number" id="userGuess" min="1" max="100">
<button onclick="checkGuess()">Submit Guess</button>
<p id="guessResult"></p>

<script>
  var randomNumber = Math.floor(Math.random() * 100) + 1;
  var guessResult = document.getElementById("guessResult");

  // Function to check if the background color is black
  function isBackgroundColorBlack() {
    var bodyStyle = window.getComputedStyle(document.body);
    var backgroundColor = bodyStyle.getPropertyValue('background-color');
    // Check if the background color is black
    if (backgroundColor === 'rgb(0, 0, 0)' || backgroundColor === '#000000' || backgroundColor === 'black') {
      return true;
    } else {
      return false;
    }
  }

  // Check and display the result
  if (isBackgroundColorBlack()) {
    document.getElementById("detectionResult").innerText = "The background color is black.";
  } else {
    document.getElementById("detectionResult").innerText = "The background color is not black.";
  }

  // Function to check user's guess
  function checkGuess() {
    var userGuess = parseInt(document.getElementById("userGuess").value);
    if (userGuess === randomNumber) {
      guessResult.innerText = "Congratulations! You guessed the correct number.";
      // Redirect to YouTube when the guess is correct
      window.location.href = "https://www.youtube.com/";
    } else if (userGuess < randomNumber) {
      guessResult.innerText = "Too low! Try a higher number.";
    } else {
      guessResult.innerText = "Too high! Try a lower number.";
    }
  }
</script>
</body>
</html>
