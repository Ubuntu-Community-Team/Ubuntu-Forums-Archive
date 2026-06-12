---
title: "SUDO APT-GET INSTALL command taking wrong IP address"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by anirudhtomer on 2009-12-28
I am trying to install the JDK for my linux ubuntu 9.10 using the command

sudo apt-get install openjdk-6-jdk

it asks me for a my password & then starts installing & then hangs at 
0%[Connecting to 10.1.25.3] 

the 10.1.25.3 is the PROXY SERVER's IP address at ma office
I use a dial up connection at my home.

I HAVE TRIED EVERYTHING TO MAKE IT WORK but it hangs at 0% 

Please help me out

---

### Post by SecretCode on 2009-12-28
In system > administration > synaptic package manager, click settings > preferences and go to the network tab. Is a proxy defined there? If so, click 'direct connection to the internet' and OK all the way out. You'll have to set it again when you're back in the office.

---

