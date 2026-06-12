---
title: "Ubuntu 9.10 boots to tty1 instead of tty7"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by dalesomers on 2010-03-13
I installed karmic on a dell vostro 1000 - all went well until I installed updates and restarted.  Ubuntu booted to tty1 instead of tty7.  I'm not entirely sure what changed, but I could do one of 2 things. at the login prompt on tty1 I could wait about 2+ minutes and it would boot to tty7 w/o my network card (but keeping the wireless) or I could ctrl+alt+f7 and get to the normal tty7 with everything working.

After a bit of looking around, i found a few solutions, but the problems were not exactly like mine.

- I could reinstall gdm (I did this and it had no effect)
- I could install minigetty and do something else (not to sure what they wanted here)
- I could remove usplash

It turned out that removing usplash did the trick...I dont get the cool little white logo over a black screen - but Ubuntu boots to tty7 at start now so I'm happy :D

---

### Post by wannianchuan on 2010-05-09
It works for me. Thank you :P

---

