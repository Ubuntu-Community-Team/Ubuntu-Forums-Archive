---
title: "Problem Installing Ubuntu 11.04"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by pyromaniacwolf1994 on 2011-07-11
Hey everyone I have an HP Pavilion Slimline desktop PC and I'm trying to install Ubuntu 11.04 via LiveCD and it won't install! I currently have Windows 7 installed, and when I reboot my computer it goes along normally, until I get to the menu where I can choose to try it, install it, or check the disks for defects...I checked the disk for defects, and it doesn't seem to have any, so I choose install Ubuntu...the only problem is, that after I do that, it looks like it's loading then it goes to a black screen which then has a bunch of text  roll past it, in about half a second, so it's too fast for me to read what it says....I have no clue what the problem is so...any suggestions? Oh and if it helps I burned the .ISO image to a Sony DVD-RW disk.

---

### Post by arena001 on 2011-07-11
I can't exactly recall  But Can you find hard disk mode or something like that in BIOS? If yes then change it to IDE and try.

---

### Post by pyromaniacwolf1994 on 2011-07-11
Okay thanks, I'll make sure to try that.

---

### Post by Mark Phelps on 2011-07-11
Next time, use Try It to boot into Ubuntu in LiveCD mode.

Then, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

If you already have the maximum of four partitions, the installer can not create any more, thus, it will not install.

---

### Post by pyromaniacwolf1994 on 2011-07-11
> **arena001 said:**
> I can't exactly recall  But Can you find hard disk mode or something like that in BIOS? If yes then change it to IDE and try.

Okay I tried that, but I couldn't find "hard disk mode" in BIOS.


> **Mark Phelps said:**
> Next time, use Try It to boot into Ubuntu in LiveCD mode.

Then, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

If you already have the maximum of four partitions, the installer can not create any more, thus, it will not install.

Okay it wouldn't even let me boot in LiveCD mode, so I tried to figure out how many partitions I have using Windows...I have 2 active partitions, and one partition made up entirely of free space.

---

### Post by arena001 on 2011-07-12
Try any other flavor of Linux and see if that works?

---

### Post by pyromaniacwolf1994 on 2011-07-12
Okay I tried OpenSUSE and that seemed to work just fine.

---

### Post by arena001 on 2011-07-12
> **pyromaniacwolf1994 said:**
> Okay I tried OpenSUSE and that seemed to work just fine.


Try downgrading to ubuntu 10.04 and see if that works (You can then upgrade to 11.04 using update manager).  If 10.04 Worked then that's a 11.04 bug.

---

