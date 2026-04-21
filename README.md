<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>AI 小遊戲</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<!-- LOGO -->
<div class="header">
    <img src="logo.png" id="logo">
    <h1>點擊方塊遊戲</h1>
</div>

<!-- 遊戲資訊 -->
<p>分數：<span id="score">0</span></p>
<button onclick="startGame()">開始遊戲</button>

<!-- 遊戲區 -->
<div id="gameArea">
    <div id="box"></div>
</div>

<script src="script.js"></script>
</body>
</html>

body {
    text-align: center;
    font-family: Arial;
    background-color: #f0f0f0;
}

/* LOGO */
#logo {
    width: 150px;
}

/* 遊戲區 */
#gameArea {
    width: 100%;
    height: 400px;
    border: 2px solid black;
    margin-top: 20px;
    position: relative;
    background-color: white;
}

/* 方塊 */
#box {
    width: 80px;
    height: 80px;
    background-color: red;
    position: absolute;
    cursor: pointer;
}

let score = 0;
let box = document.getElementById("box");
let gameStarted = false;

function moveBox() {
    let gameArea = document.getElementById("gameArea");

    let x = Math.random() * (gameArea.clientWidth - 80);
    let y = Math.random() * (gameArea.clientHeight - 80);

    box.style.left = x + "px";
    box.style.top = y + "px";
}

function startGame() {
    score = 0;
    gameStarted = true;
    document.getElementById("score").innerText = score;
    moveBox();
}

box.addEventListener("click", function() {
    if (!gameStarted) return;

    score++;
    document.getElementById("score").innerText = score;
    moveBox();
});
