---
title: "Error while installing 10.10"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by nscherneck on 2011-03-09
I'm getting an error while installing Ubuntu 10.10 (see attached pic). I first tried to set partitions manually and when I received the error I selected to use the entire disk hoping allowing Ubuntu to set partitions would resolve the issue. Got the same/similar error. Any ideas? Thanks in advance...

---

### Post by Hakunka-Matata on 2011-03-09
More information please:  Installing from USB?, CD, PXE 

sdb means you have at least two HDDs, a little more information

---

### Post by nscherneck on 2011-03-09
Ah yes, my apologies. And thank you for the response. I'm using a Live CD, booting to the CD-ROM. I've checked the md5sum and have run (not installed) the OS from this Live CD on another machine.
 
System info:
Dell Optiplex GX150 desktop
Intel Pentium 3 996MHz
256Mb RAM
(2) 20Gb Maxtor HD (IDE)
Running Windows XP Professional SP2 on one drive, attempting to install Ubuntu on the other
Note: this desktop cannot boot to USB

---

### Post by Hakunka-Matata on 2011-03-09
post output of these commands please:
[LIST]
[*]> df -h
[*]> sudo fdisk -lu
[/LIST]

so we can see what kind of partitioning exists on your two HDDs

---

### Post by nscherneck on 2011-03-09
Hakunka, do I run these commands in a terminal within Ubuntu from the Live CD or elsewhere?

---

### Post by Hakunka-Matata on 2011-03-09
Yes, from the Terminal

to avoid typos it's often easier to copy the commands and paste into terminal.  If you use Keyboard to paste into terminal, the paste command is CTRL - SHIFT - V

---

