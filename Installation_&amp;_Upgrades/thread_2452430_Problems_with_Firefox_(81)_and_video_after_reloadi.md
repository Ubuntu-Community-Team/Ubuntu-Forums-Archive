---
title: "Problems with Firefox (81) and video after reloading 20.04"
date: 2020-10-21
forum: Installation &amp; Upgrades
---

### Post by deck on 2020-10-21
Due to really dorking my system up I reloaded 20.04.1 (except my home directories).  I did not do updates while reloading because that caused problems on one attempt.  After getting the system reloaded, I ran the Software Updater to get to the most current versions of programs.  When I went to Youtube, I kept getting messages that Firefox did not support the video format.  One Youtube channel in particular I go to is Lab Padre since I am a SpaceX fan on which I get the video message.

What am I missing.  It would seem that there is some dependency that is not being met.  However, I don't know how to figure out what it is.

---

### Post by CelticWarrior on 2020-10-21
[https://support.mozilla.org/en-US/questions/1177497](https://support.mozilla.org/en-US/questions/1177497)

---

### Post by deck on 2020-10-22
Thanks CelticWarrior.  Unfortunately that didn't work as I had no Flash player installed.  I did another web search (I don't google) and found the answer:

>sudo apt install libavcodec-extra

After doing this and restarting Firefox all is good.

---

