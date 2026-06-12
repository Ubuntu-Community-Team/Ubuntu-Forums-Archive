---
title: "screen resolution stuck at 840x680"
date: 2020-09-23
forum: Installation &amp; Upgrades
---

### Post by sanjay_thomaspg on 2020-09-23
Hello Sir, 
 My system configuration is ASUS m4n68T-MLE mother board AMD Phenom II x2 555 processor Nvidia  c61 Geforce 7025/nForce 630a graphics..After installing Ubuntu 20.04 along with windows 10..
Following problems are occurred
1.after installation on first login screen is freezy showing multiple resolution option but  system getting hang after two or more application  opening
 2.so to solve above problem.. I tried to install NVIDIA drive 440 through terminal..Ubuntu screen goes blank and black screen  and showing  different resoultion number displaying on  screen


3.so I make fresh installation again, and tried to disable nouveau driver.. then system showing only one resolution 840x680...


  so please help me to solve the issue and install correct driver in ubuntu 20.04

---

### Post by CelticWarrior on 2020-09-23
**There are no Nvidia drivers for your legacy chipset/iGPU.**

It either works with the default open-source nouveau or it doesn't.
Standard Ubuntu (with Gnome) is definitely NOT recommended for such old hardware. Try Lubuntu or any other lighter DE based Ubuntu flavor or Debian or other, just NOT standard Ubuntu.

---

