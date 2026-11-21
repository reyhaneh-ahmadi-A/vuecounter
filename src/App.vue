
<script setup>
import { ref } from 'vue'

const count = ref(0)
const totalClicks = ref(0)

function increase() {
  count.value++
  totalClicks.value++
}

function decrease() {
  count.value--
  totalClicks.value++
}

function reset() {
  count.value = 0
  totalClicks.value = 0
}
</script>

<template>
  <main class="dashboard">
    <div class="background-glow"></div>

    <header class="topbar">
      <div class="brand">
        <span class="brand-icon">✦</span>
        <span>GAME<span class="green">COUNTER</span></span>
      </div>

      <div class="status">
        <span class="status-dot"></span>
        SYSTEM ONLINE
      </div>
    </header>

    <section class="counter-section">
      <div class="eyebrow">
        <span></span>
          
        <span></span>
      </div>

      <h1>COUNT YOUR <span>POWER</span></h1>

      <p class="subtitle">
        Take control. Keep counting. Break your limits.
      </p>

      <div class="counter-card">
        <div class="card-top">
          <span>LIVE COUNTER</span>
          <span class="live">
            <span></span> LIVE
          </span>
        </div>

        <div class="number-box">
          <span class="number">{{ count }}</span>
        </div>

        <div class="counter-info">
          <span>YOUR CURRENT SCORE</span>
          <span>#{{ String(Math.abs(count)).padStart(4, '0') }}</span>
        </div>

        <div class="buttons">
          <button class="action-btn minus" @click="decrease">
            <span>−</span>
            DECREASE
          </button>

          <button class="action-btn plus" @click="increase">
            <span>+</span>
            INCREASE
          </button>
        </div>

        <button class="reset-btn" @click="reset">
          ↻ RESET COUNTER
        </button>
      </div>

      <div class="stats">
        <div class="stat-box">
          <span class="stat-icon">◈</span>
          <div>
            <strong>{{ totalClicks }}</strong>
            <small>TOTAL CLICKS</small>
          </div>
        </div>

        <div class="stat-box">
          <span class="stat-icon">⚡</span>
          <div>
            <strong>{{ count >= 0 ? 'POSITIVE' : 'NEGATIVE' }}</strong>
            <small>COUNTER STATUS</small>
          </div>
        </div>
      </div>
    </section>

    <footer>
      <span>GAMECOUNTER SYSTEM v1.0</span>
      <span>DESIGNED FOR GAMERS <b>●</b></span>
    </footer>
  </main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Inter:wght@400;500;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #070d17;
  font-family: 'Inter', sans-serif;
}

.dashboard {
  min-height: 100vh;
  width: 100%;
  background:
    radial-gradient(ellipse at 50% 45%, #12263a 0%, transparent 50%),
    #070d17;
  color: #fff;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 30px 7%;
}

.background-glow {
  position: absolute;
  width: 500px;
  height: 500px;
  background: #00ff9d;
  opacity: 0.035;
  filter: blur(140px);
  border-radius: 50%;
  top: 20%;
  pointer-events: none;
}

.topbar {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  z-index: 2;
}

.brand {
  font-family: 'Orbitron', sans-serif;
  font-size: 19px;
  font-weight: 800;
  letter-spacing: 2px;
}

.brand-icon {
  color: #00ff9d;
  margin-right: 10px;
  font-size: 25px;
}

.green {
  color: #00ff9d;
}

.status {
  color: #8294a9;
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 2px;
}

.status-dot,
.live span {
  display: inline-block;
  width: 7px;
  height: 7px;
  background: #00ff9d;
  border-radius: 50%;
  margin-right: 7px;
  box-shadow: 0 0 10px #00ff9d;
}

.counter-section {
  z-index: 2;
  width: 100%;
  max-width: 550px;
  text-align: center;
  padding: 30px 0;
}

.eyebrow {
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 4px;
  color: #00ff9d;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
}

.eyebrow span {
  width: 25px;
  height: 1px;
  background: #00ff9d;
}

h1 {
  font-family: 'Orbitron', sans-serif;
  font-size: clamp(24px, 3.5vw, 39px);
  font-weight: 900;
  margin-top: 20px;
  letter-spacing: 1px;
}

h1 span {
  color: #00ff9d;
}

.subtitle {
  color: #8090a5;
  font-size: 13px;
  margin-top: 12px;
  letter-spacing: 0.5px;
}

.counter-card {
  margin-top: 38px;
  background: linear-gradient(145deg, #111f30, #0b1421);
  border: 1px solid #1e3946;
  border-radius: 18px;
  padding: 28px 35px;
  box-shadow: 0 20px 70px #0008, 0 0 30px #00ff9d08;
  position: relative;
}

.card-top,
.counter-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 2px;
  color: #71869a;
}

.live {
  color: #00ff9d;
  font-size: 9px;
}

.live span {
  width: 6px;
  height: 6px;
}

.number-box {
  margin: 25px 0;
  padding: 25px;
  border-radius: 12px;
  background: #070f19;
  border: 1px solid #1c3541;
  box-shadow: inset 0 0 30px #0008;
}

.number {
  font-family: 'Orbitron', sans-serif;
  font-size: clamp(65px, 10vw, 100px);
  font-weight: 800;
  color: #00ff9d;
  text-shadow: 0 0 15px #00ff9d55;
  overflow-wrap: anywhere;
}

.counter-info {
  font-size: 9px;
  letter-spacing: 1px;
}

.counter-info span:last-child {
  color: #00ff9d;
}

.buttons {
  display: flex;
  gap: 12px;
  margin-top: 28px;
}

.action-btn {
  flex: 1;
  height: 58px;
  border-radius: 9px;
  font-family: 'Orbitron', sans-serif;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 1px;
  cursor: pointer;
  transition: 0.25s;
}

.action-btn span {
  font-size: 22px;
  margin-right: 7px;
  vertical-align: middle;
}

.plus {
  background: #00ff9d;
  color: #07150f;
  border: 1px solid #00ff9d;
}

.minus {
  background: transparent;
  color: #00ff9d;
  border: 1px solid #00a96a;
}

.plus:hover {
  background: #fff;
  box-shadow: 0 0 25px #00ff9d55;
  transform: translateY(-3px);
}

.minus:hover {
  background: #00ff9d12;
  box-shadow: 0 0 20px #00ff9d33;
  transform: translateY(-3px);
}

.reset-btn {
  width: 100%;
  margin-top: 15px;
  height: 42px;
  border: 1px solid #25394a;
  background: #101b29;
  color: #8295a9;
  border-radius: 8px;
  cursor: pointer;
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 2px;
  transition: 0.2s;
}

.reset-btn:hover {
  color: #fff;
  border-color: #00ff9d;
}

.stats {
  display: flex;
  gap: 15px;
  margin-top: 18px;
}

.stat-box {
  flex: 1;
  background: #101c2a;
  border: 1px solid #1d3342;
  border-radius: 10px;
  padding: 15px;
  display: flex;
  align-items: center;
  gap: 13px;
  text-align: left;
  min-width: 0;
}

.stat-icon {
  color: #00ff9d;
  font-size: 24px;
}

.stat-box div {
  display: flex;
  flex-direction: column;
  gap: 5px;
  min-width: 0;
}

.stat-box strong {
  font-family: 'Orbitron', sans-serif;
  font-size: 13px;
  color: #fff;
}

.stat-box small {
  font-size: 9px;
  letter-spacing: 1px;
  color: #71869a;
}

footer {
  width: 100%;
  display: flex;
  justify-content: space-between;
  color: #52657a;
  font-family: 'Orbitron', sans-serif;
  font-size: 9px;
  letter-spacing: 1.5px;
  z-index: 2;
}

footer b {
  color: #00ff9d;
  margin-left: 5px;
}

@media (max-width: 600px) {
  .dashboard {
    padding: 22px 16px;
  }

  .brand {
    font-size: 14px;
  }

  .status {
    font-size: 8px;
  }

  .counter-card {
    padding: 22px 16px;
  }

  .stats {
    flex-direction: column;
  }

  footer {
    font-size: 7px;
  }
}
html,
body,
#app {
  width: 100%;
  min-width: 100%;
  min-height: 100%;
  margin: 0;
}

#app {
  max-width: none !important;
  padding: 0 !important;
}

.dashboard {
  width: 100%;
  min-height: 100vh;
  margin: 0 auto;
}
</style>
