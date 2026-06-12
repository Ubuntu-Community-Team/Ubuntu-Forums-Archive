---
title: "Ubuntu won't display"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Mutch on 2006-03-10
Hi, im a linux noob, i recently have decided to change to linux. And after looking around, i decided ubuntu had an awesome community so i decided to give it a whirl. :)

I installed ubuntu fine, but when i ran it after loading all the modules my screen went blank and said could not display, my second monitor had a whole bunch of coloums with different colors. I ran the live cd to the same effect. Does this mean im McScrooged? 

Im running a Dell 2405FPW (24inch lcd) as my primary and a 17inch crt as a secondry monitor. All of a Geforce FX5700le. 2.4gh p4 and a gig of ram.

THanks in advance
mutch

---

### Post by dermotti on 2006-03-10
sudo dpkg-reconfigure xserver-xorg

when selecting a driver, try using "vesa"

startx

---

