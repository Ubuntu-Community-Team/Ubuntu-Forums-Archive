---
title: "Installing Xubuntu, no partitions"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by pehrlabel on 2007-09-05
Hello I'm trying to install feisty xubuntu on a compaq pIII laptop that used to have windows ME. The laptop has been f:disced, so when I start up the bios the computer says "no operating system," which i thought was good, and would be a clean start for xubuntu.

but when i start the xubuntu installer from the livecd, it only gets to step 4. the only choice for partitioning is "manual", so i choose that and then go to the next step. but when the screen for choosing a partition shows up, it doesn't offer me any choices of partitions; it's empty. and at that point i have to stop the wizard, there's nothing further i can do.

anyone have a tip on how i can get this to install? 

on a side note, running xubuntu from the live disc makes my monitor act strange: there is a column in the middle of the screen in which everything disappears, so if i drag a window sideways thru the column, it disappears, but then it pops up on the other side, as a double of the image on the left, just offset by a little. this doesn't bother me if we can fix my first problem, though! 

thanks! adam
:KS

---

### Post by Pumalite on 2007-09-05
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Boot from it make a large partition of your hard drive, format it ext3 and install >Guided>Use Entire Disk.

---

### Post by mocoloco on 2007-09-05
Within your live session of Xubuntu you can install gparted, open synaptic and search for it.

---

### Post by pehrlabel on 2007-09-05
Thanks! I'm downloading it right now. I'll try it and post back soon.

---

### Post by pehrlabel on 2007-09-06
Hmm... well i downloaded a gparted disc and ran it, but it couldn't detect any devices to build a partition on. Now i'm thinking this is becoming a laptop problem, not a xubuntu problem. does anyone have any advice on how i can get my hard drive detected? since this is a hand-me-down laptop from 8 years ago i can just throw it away if this is doesn't work out... but if this might work it could be cool.

I went into my Phoenix BIOS, but it didn't have any options for devices, it only allowed me to set system date/time and to change the boot order of my floppy, hard drive, and dvd drive.

---

