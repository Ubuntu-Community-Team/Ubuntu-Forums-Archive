---
title: "how to boot windows"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by bugsycleave on 2005-06-17
I have installed ubunto and love it but i can no longer find windows or boot it. :???:   please help.  I know it still exists and i have created a new partition for linux but i can't find windows or boot it.  POlease help

---

### Post by pietro_spina on 2005-06-17
There should be a text menu (called a grub menu) that comes up for a few seconds when you start up your computer... you should be able to use you arrow down key to select Windows (If it was seen by the Ubuntu installer)

also search these forums for terms like 

dual boot
grub
mbr
master boot record

and my favorite.... "help help I borked my Ubuntu with windowsXP" :smile:

-p

---

### Post by wylfing on 2005-06-17
This is a real tangle of a problem, and a given solution won't always work for you. The first thing you should do is search these forums for advice on this problem. There have been many people in the same boat as you. I'm sure you can find some results if you search for them.

Now, to be specific, I had this happen to a Win2K box where I installed Ubuntu on a 2nd disk. I installed GRUB to the MBR (I bet you did too) and thereafter could not boot Windows. What worked for me was to go into BIOS and set the main hard disk from "auto" to "LBA". After that, GRUB booted Windows just fine. YMMV.

---

