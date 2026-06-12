---
title: "What is my CPU frequence?"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-30
Hi Ubuntu Experts :)

I have performed a server installation on my brand new IBM X31 laptop. Besides that I have installed 'powernowd' to control my CPU's frequency (Centrino, Pentium M). But I would like to see, that it is really working and adjusting the speed according to the work it haft to do. I have installed Gnome and know that there is a frequency display program for the kicker. But it seems that some dependencies are missing (Ubuntu error?) which results in some ACPI errors and missing applets for the kicker. So I'm going to install Xfce instead. I'm sure it will work alright if I perform a normal installation - but I don't want all that out-dated software like OpenOffice, Firefox etc.

So want i'm looking for, is a simple program (for X or Console) that can tell me what frequency my processor is running)

  - Thanks in advance :-)

---

### Post by jemt on 2005-07-30
I just found out that 'hwinfo' could tell what frequence my CPU was running.

'hwinfo' <enter>

Find "cpu MHz" - There you got it :)

---

### Post by jemt on 2005-07-30
You could probably also just do a :

'nano /proc/cpuinfo'

---

