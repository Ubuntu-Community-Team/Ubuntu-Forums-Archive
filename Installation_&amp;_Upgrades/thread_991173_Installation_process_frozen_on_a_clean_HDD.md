---
title: "Installation process frozen on a clean HDD"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by qkumbr on 2008-11-23
I am trying to install Ubuntu on a freshly cleaned HDD and the installation freezes at the same point every time. Here's my situation:

-Formatted a 160GB SATA HDD with Darik's Boot and Nuke.
-Burned ubuntu-8.10-desktop-i386.iso onto a CD-R using Roxio. WinXP, SP2.
-Booted with only the clean HDD attached, on SATA2. The SATA1 connecter on my motherboard is broken. No other HDDs are attached.
-Gets past the Ubuntu loading bar, then it gets to:
[   362.368296] ---[ end trace 7e259dblahblahblah ]---
Here, I left my computer on for an hour or two, and nothing else happened.
-I restart my system and it can't boot from the HDD.

I ran the "Check CD for errors" utility and it found errors with 3 files. I burned a second CD-R with Alcohol 120% and the same thing happened.

I cannot boot Ubuntu off of the CD. It gets past the Ubuntu loading bar, then stays on a black screen. Waited an hour and nothing happened.

Pentium 4, 3.06 GHz
2.24 GB RAM
On-board graphics
WD 160GB SATA HDD

Any help is much appreciated. I have been meaning to install Linux and try it out for the longest time and I don't want to give everything up here. Are there known errors with the .iso I downloaded?

---

### Post by Rabindranath on 2008-11-23
Try downloading the ISO file with bittorrent. Check the MD5 sum with any MD5 checking tool. Burn the ISO with infrarecorder. Or use Unetbootin to make a bootable USB. This removes any problem in the CD or in the CD drive and installation is much faster. 

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

I installed ubuntu in 5 min 43 secs through USB. :)

---

