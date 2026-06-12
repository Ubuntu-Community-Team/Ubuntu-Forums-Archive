---
title: "Gutsy install CD not working on Acer Aspire 1360"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by asdir on 2007-11-02
The GUI doesn't start neither in the normal mode nor in safe graphics mode when I boot from CD. 
In normal mode it tells me that it will work in low graphics mode unless I configure it myself, but none of the options help. Its always a blank screen afterwards or back to non-graphics-mode and a total stop after a while.
In the safe graphics mode xorg at least tries to start the server a couple of times, before resignating with a message that tells me that "somethign bad is going on" and that it will go on trying after a while, which it doesn't.

Knoppix and Dapper work, I will try Feisty when I am finished downloading it, but it would be a lot nicer to be able to install Gutsy from CD.

Any takers?

Thx so far

Update: Feisty could be installed flawlessly and is working well. Will try updating tomorrow and report again.
UpdateUpdate: I never tried to upgrade to Gutsy in the end. In case it didn't work I did not want to waste the time reinstalling the system. However, I still would like to know if it someone with similar problems could upgrade flawlessly. Is this bug (I assume it is one) filed somewhere?

---

### Post by asdir on 2007-12-17
BUMP

(And additional info: I checked the MD5-Checksum, the CD is burned correctly.)

---

### Post by smospatat on 2008-01-13
It's a problem with xorg

when the system hangs, press Alt+F1
login

run:
dpkg-reconfigure xserver-xorg

and follow the steps

when finished, run 
startx

that should do the trick


or, alternatively, you can use the alternate install cd

---

### Post by asdir on 2008-01-20
Do I have to follow these steps again when Gutsy is finally installed on the hard drive? Or will it run without further configuration once it is installed?
I am asking because I could install it via update since Feisty is already there.

---

### Post by prlancas on 2008-03-09
I have an Acer Aspire 1360 and have had no problems installing apart from something strange where the screen is blank. I just switched to the console (ctrl+alt+f1) then back to X (ctrl+alt+f7) . It was fine after that and had no problems with the installed version.

Have you got your wireless networking working with suspend in any version of ubuntu? When I have it enabled using the ndiswrapper neti2220 driver it suspends but will not wake up.

---

### Post by Pumalite on 2008-03-09
How large is your /swap compared to your RAM?

---

