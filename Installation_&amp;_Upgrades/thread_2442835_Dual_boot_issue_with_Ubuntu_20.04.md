---
title: "Dual boot issue with Ubuntu 20.04"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by ninadk on 2020-05-08
Hi, 


I am a big ubuntu fan and currently, I am holding Lenovo X1 extreme gen 1 laptop. I was able to install Ubuntu 20.04 along with Windows 10 OS. When my BIOS graphics mode is "discreet" then both OS works perfectly but if I change it to "Hybrid" then my ubuntu freezes. That's why I had to use Pop OS. If I use Ubuntu 20.04 in Discreet graphic mode then my battery consumption is high. Is there any way to run Ubuntu 20.04 in Hybrid graphics mode? 

Thanks in advanced.

---

### Post by CelticWarrior on 2020-05-09
Welcome.

Yes, of course Ubuntu can run with either iGPU Intel or dGPU Nvidia as long as it has the proper graphics drivers (for Nvidia) installed and Secure Boot disabled in UEFI (what you call "BIOS" but it's not, your computer like any other from the last 10 years no longer has BIOS, it has UEFI instead).

---

