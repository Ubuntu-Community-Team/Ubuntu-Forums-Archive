---
title: "Trouble instaling ubuntu"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Edmundas on 2010-03-19
Hey, I tryied to install the Ububtu 9.10 while dual booting with win xp, then i booted from a cd I pressed install, and that's where my promlems begin, i just got a white Ubuntu logo on black background and nothing happens, what could be wrong, and what could i do? Because I downloaded the Ubuntu from their main site, I also have the older version of Ubuntu 7.04 and it installs normaly so maybe i should try installing the older version like 9.04 and try to upgrade ?

---

### Post by zvacet on 2010-03-19
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before burning iso?If md5sum doesn't match and you still have iso download same iso with torrent and point download to the folder with your existing iso.Torrent will just check iso for bad files and replace them with good ones.After that run md5sum again.Burn iso on lower possible speed.

---

### Post by tommcd on 2010-03-19
> **Edmundas said:**
> ... i booted from a cd I pressed install, and that's where my promlems begin, i just got a white Ubuntu logo on black background and nothing happens, what could be wrong, ...
The first step for troubleshooting problems with booting from the CD should always be to check the CD for defects?
Are you at least able to get to the Ubuntu desktop when you boot from the CD? Since you said "i booted from a cd I pressed install", I assume you did. Is that correct? Are able to get to the 2nd screenshot on this tutorial:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala)
If so, then first run the option to "check disc for defects". If the CD check passes, then the disc is good.
Write back with the results.
Also what graphics card do you have?

And welcome to the Ubuntu forums!

---

### Post by Edmundas on 2010-03-19
**** I forgot to write it on low speed :/ Thx well what was a fail :/:KS

---

### Post by tommcd on 2010-03-19
> **Edmundas said:**
> **** I forgot to write it on low speed :/ Thx well what was a fail :/:KS
So did the disc check fail? 
If you are burning the Ubutnu CD from a Windows system, try using Iso Recorder or Infra Recorder. And burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then boot up the CD and run the option "check disc for defects" again. If it passes, then proceed with the install.
EDIT: If you are using Windows 7, then just right-click on the iso image and choose: "burn disc image" as it says in that "Burning Iso How To" tutorial I linked to.
Write back if you need more help.

---

