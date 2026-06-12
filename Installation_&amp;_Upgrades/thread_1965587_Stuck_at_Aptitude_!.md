---
title: "Stuck at Aptitude !"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by dchen on 2012-04-26
Tried to install Ubuntu 11.10 server from CD, after choosing the software to be installed, it displayed the Aptitude menu with the following on the screen:

  --- Installed packages (188)
  --- Not installed packages (960)
  --- Virtual packages (375)
  --- Tasks (1916)

There are a few command letters on the top of screen allow you to take some actions, i.e. g: Download/Install/Remove pkgs, ...

'm not familiar with the Aptitude at all, **what should I do in response to this Aptitude screen** ?
initially I pointed to the "Installed packages (188)" line and did "g" then "g", and got many errors,...
then tried to point to the "Not installed packages (960)" line, got too many errors too, ...

Also the explanation of "--- Installed packages (188)" or "--- Not installed packages (960)" was not so great ! May I just quit the Aptitude entirely ?  Aptitude is the stopper for the beginner of Ubuntu 11.x server !

---

### Post by dino99 on 2012-04-26
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by raja.genupula on 2012-04-26
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

---

