<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Be My Valentine ❤️</title>
<style>
body{
    margin:0;
    font-family:'Arial', sans-serif;
    background: linear-gradient(135deg,#ff9a9e,#fad0c4);
    text-align:center;
    color:white;
    overflow-x:hidden;
}

.page{
    width: 100%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 50px 20px;
    box-sizing: border-box;
    position: relative;
}

h1{
    font-size: 40px;
    margin-bottom: 40px;
}

button{
    padding:15px 30px;
    font-size:20px;
    border:none;
    border-radius:12px;
    margin:15px;
    cursor:pointer;
    transition:0.3s;
    position: relative;
}

.yes{
    background:#ff4d6d;
    color:white;
}

.no{
    background:white;
    color:#ff4d6d;
}

#letter{
    max-width:800px;
    font-size:18px;
    line-height:1.7;
    background: rgba(255,255,255,0.2);
    text-align:left;
    padding:25px;
    border-radius:20px;
}

#insist{
    margin-top: 30px;
    font-size: 24px;
    display:none;
}

.heart {
    position: absolute;
    font-size: 24px;
    color: #ff4d6d;
    animation: floatUp 3s linear forwards;
}

@keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity:1;}
    100% { transform: translateY(-500px) scale(1.5); opacity:0;}
}
</style>
</head>
<body>

<!-- PAGE 1 : Question -->
<div class="page" id="page1">
    <h1>Will you be my Valentine? 💖</h1>
    <button class="yes" onclick="goToPage2()">Yes ❤️</button>
    <button class="no" id="noBtn">No 😢</button>
    
    <div id="insist">
        Be my Valentine right now! ❤️<br>
        <button class="yes" onclick="goToPage2()">Yes ❤️</button>
        <button class="yes" onclick="goToPage2()">Yes ❤️</button>
    </div>
</div>

<!-- PAGE 2 : Fun Message -->
<div class="page" id="page2" style="display:none;">
    <h1>I knew you loved me 😍🤭</h1>
    <p style="font-size:24px;">Have a little something for you! Wanna see it?</p>
    <button class="yes" onclick="goToLetter()">Yes ❤️</button>
    <button class="yes" onclick="goToLetter()">Yes ❤️</button>
</div>

<!-- PAGE 3 : Letter -->
<div class="page" id="page3" style="display:none;">
    <h1>My Dear Sarah 💌</h1>
    <div id="letter">
        <p>
        Happy Valentine’s Day, my love.<br><br>
        It’s been two years now — two years of us. When I think about it, it feels both long and short at the same time. Long, because we’ve been through so many little moments, worries, laughs, misunderstandings, and reconciliations together… and short, because I still feel like our real story is only beginning.<br><br>
        We never really had the chance to spend much time just the two of us. Life, circumstances, and especially the rules at home haven’t always made things easy for us. Sometimes I wish I could simply walk beside you, hold your hand outside without thinking, or sit and talk for hours without watching the time. But even without that, we stayed. We didn’t give up on each other — and to me, that means our feelings are real.<br><br>
        I know you can get mad very quickly, sometimes for the smallest things. I won’t lie — sometimes I don’t understand it at all. But even in those moments, I don’t stop loving you. Because behind that temper, I know there is a girl who cares deeply, who feels strongly, and who is afraid to lose what she loves. And I want you to know: I’m still here.<br><br>
        What I love most about us is that, despite the distance, the limits, and the frustrations, we never lost hope. We always found our way back to each other. That’s why I believe in us. Not because everything is perfect, but because even when it’s difficult, we still choose one another.<br><br>
        I don’t know exactly what the future will look like. But I do know one thing: one day we will finally get the simple moments we’ve been waiting for — real conversations side by side, real walks, real memories together. And when that day comes, it will mean even more because of everything we went through to get there.<br><br>
        Thank you for these two years, for your patience, for your effort, and even for your little jealous or angry moments — they remind me how much you care. You are important to me, more than you probably realize.<br><br>
        Happy Valentine’s Day again, Sarah.<br>
        No matter the distance or the obstacles, I still choose you.
        </p>
    </div>
</div>

<script>
const noBtn = document.getElementById("noBtn");
const insistDiv = document.getElementById("insist");
let noCount = 0;

// Déplacer le bouton No
function moveNo(){
    const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
    const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
    noBtn.style.position = "absolute";
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
}

// Compteur et déclenchement du message insistant
function handleNo(){
    noCount++;
    if(noCount >=5){
        insistDiv.style.display = "block";
        noBtn.style.display = "none"; 
    } else {
        moveNo();
    }
}

noBtn.addEventListener("mouseover", handleNo);
noBtn.addEventListener("click", handleNo);

// Affiche la page 2
function goToPage2(){
    document.getElementById("page1").style.display = "none";
    const page2 = document.getElementById("page2");
    page2.style.display = "flex";
    createHearts(); // lance les cœurs
}

// Affiche la page 3
function goToLetter(){
    document.getElementById("page2").style.display = "none";
    document.getElementById("page3").style.display = "flex";
}

// Créer des cœurs flottants sur la page 2
function createHearts(){
    const page2 = document.getElementById("page2");
    for(let i=0;i<30;i++){
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "❤️";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.fontSize = (15 + Math.random()*25) + "px";
        heart.style.animationDuration = (3 + Math.random()*3) + "s";
        page2.appendChild(heart);

        // Supprime le coeur après l'animation
        setTimeout(()=> page2.removeChild(heart), 4000);
    }
}
</script>
</body>
</html>
