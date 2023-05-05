Download Link: https://assignmentchef.com/product/solved-cse270e-final-project-an-application-to-create-a-shared-game-of-tictactoe
<br>
<h1></h1>

In this program you will create an application to create a shared game of tictactoe. Multiple pairs of people should be able to play at the same time.




GamePlay Overview:

<ul>

 <li>Initial Page:

  <ul>

   <li>Shows an input for userName and a box for gameID.</li>

  </ul></li>

</ul>

○    To start a totally new game the user will enter their userName and leave the GameID empty. This will cause the system to return a gameID.

○    The first player will give their partner the gameId.

○    The second player will enter their name and the gameId.

<ul>

 <li>This will commence the game:</li>

 <li>Player1 will be prompted to select a square and will send a move api call.

  <ul>

   <li>if its invalid player1 will receive an error message</li>

  </ul></li>

 <li>Player2 wil then be prompted to move</li>

 <li>Play will continue until someone wins or there is a draw (all squares filled)</li>

 <li>At that point each player will be given a score screen showing their and all other players scores as well as an option to play each other again or to play a new game.</li>

</ul>




This assignment will be done in multiple parts.

<ul>

 <li>In Assignment 14 you will focus on the datamodel. ● In Assignment 15 you will focus on the API</li>

 <li>In the final project you will focus on the Client Side</li>

</ul>




Assignment Details:

<ul>

 <li>Create a new directory called Assignment-14</li>

 <li>In this directory create a directory called model and test. Put your data model code in the directory model (called game.js) and your mocha tests in test directory.</li>

 <li>Make sure this is in git.</li>

</ul>




For Assignment 14:

You will first create a series of Mocha/Chai tests to get ready for your code.  You will put these in git and submit Assignment-13-tests for me to approve.  You may start on the actual datamodel code while I am approving the tests but it might take you several iterations to get the tests approved.




Data Model Details:

<ul>

 <li>gameSchema

  <ul>

   <li>gameId: String//random 6 letter, lower case string to identify game. You create thi sincode</li>

  </ul></li>

</ul>

○    player1Name: String

○    player2Name: String

○    moveCnt: Number

○    lastMoveTime: Number -&gt; localtime, seconds when last move was updated

○    board: [Number] -&gt; array of 9 number representing board

○    0 1 2

○    3 4 5

○    6 7 8

○    state: String // waiting, player1Turn, player2Turn, player1Win, player2Win, stalemate




functions:

<ul>

 <li>async function createId()

  <ul>

   <li>function to create a randome game id and make sure it does not exist in the database</li>

  </ul></li>

 <li>function getGame(gameId)

  <ul>

   <li>returns a promise to find the game given the game id</li>

  </ul></li>

 <li>function newGame(playerName, gameId)

  <ul>

   <li>returns a promise to setup a new game. See writeup for details</li>

  </ul></li>

 <li>function move(gameId,playerName,move)

  <ul>

   <li>gameId -&gt; id of valid game</li>

  </ul></li>

</ul>

○    playerName -&gt; string name of player

○    move – 0-8 indicating which square player moves to ○         returns a promise to make a move:

■    if ok: returns the gameModel

■    if error calls reject with an error message.

○    example errors: trying to move when not your turn, trying to move when game won…

<ul>

 <li>function getGames

  <ul>

   <li>returns promise to return an array of games. Please make sure to delete the gameID from the individual games so people can’t hijack other games.</li>

  </ul></li>

 <li>async function clear -&gt; I added this helper function to clear out the database for testing</li>

 <li>function testAdd(gameSchemaInstance)

  <ul>

   <li>I added this helper function to directly create a game instances.</li>

  </ul></li>

</ul>

○    Used for testing.

○    Returns a promise to add the data.







Step1:

<ul>

 <li>Create tests using Mocha and Chai to test this api.</li>

 <li>Create a strong suite of tests that will prove the datamodel.</li>

 <li>Create these in test/*.js</li>

 <li>Add these tests to git</li>

 <li>submit this to Assignment-14-tests</li>

</ul>




Step2:

<ul>

 <li>Build the data model. It should pass all the tests you created.</li>

 <li>Submit the code to git</li>

 <li>submit a link to canvas Assignment-14-data</li>

</ul>







<h1>For Assignment 15</h1>

Copy over Assignment-14 to Assignment-15 in your working copy on on git.




Using express, create the following API’s that will invoke the data models created in the previous assignment:




<ul>

 <li>GetGames

  <ul>

   <li>url: /api/v1/games</li>

  </ul></li>

</ul>

○    method: get ○  json_in: N/A ○    json_out:

■    {games:[game1,game2…]|

■    please make sure that no gameId’s are returned, simply return “” for gameId for all games

<ul>

 <li>play

  <ul>

   <li>this method is invoked to start a game</li>

  </ul></li>

</ul>

○    url: /api/v1/game

○    method: post

○    json_in: {playerName: String, gameID: String}

○    json_out: {status: OK or FAIL, msg=String, game: gameSchema for existing game

<ul>

 <li>move

  <ul>

   <li>this method is invoked to make a move</li>

  </ul></li>

</ul>

○    url: /api/v1/move/:gameID/:playerName/:movePosition

○    method: get

○    json_in: none

○    json_out: {status: OK or FAIL, msg=String, game: gameSchema for existing game ●      More Details

○    Also create a series of SuperTests for testing the api. Make sure to document and include these tests in your git.

○    These tests (and of course the code) should include security tests to make sure your api properly sanitizes and escapes user input.

○    Run this server on port 3015

○    submit a link to the api and to your git repo.




<h1>For Final Project</h1>

Copy over Assignment-15 to FinalProject

I am providing in my public git the html and javascript files to play the game. I have not heavily tested this code so make sure it works and fix bugs.

<u><a href="https://gitlab.csi.miamioh.edu/campbest/cse270e-campbest-public">https://gitlab.csi.miamioh.edu/campbest/cse270e-campbest-public</a></u>




There is a “manage boards” link at the bottom of the page.




You are to create a nodejs based page (eg: Not using ajax) management menu page with links to the following: Each are separate pages

<ul>

 <li>Statistics page: Create a table that lists each player, how many times have they won and lost and their percentages.</li>

 <li>Page that lists all games and their details. eg: player1name,player2name, outcome, number moves and the final board. (board should be shown as a tic-tac-toe board, not an array).</li>

 <li>In Progress list: Create a table that lists all games that are in progress: eg: are not won, lost or stalemated. List game details of names and time of last move.</li>

 <li>Orphaned game list: create a table that lists all games in the waiting state and the time they were created along with player1name.</li>

 <li>Page to clear out old games. It should have a form that lists a date and will clear out all games that are older than that date. This page should require a password to clear out the data and the password shall be “CLEAR”.</li>

</ul>


