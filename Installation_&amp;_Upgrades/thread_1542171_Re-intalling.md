---
title: "Re-intalling"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Arnoxsas on 2010-07-30
Hi all, i have some problem, i want to change my os from Linux to windows, only to see witch one is faster. So i have ubuntu 10.04 and then im doing restart, for me need press F11 to boot menu, and F2 to bios, but f11 and F2 not working, pressing it very long but it still not working. can some one say how to fix it? Please.

P.S Sorry for bad english, it my second language.

---

### Post by ajgreeny on 2010-07-30
Do you see a grub menu when you boot up the computer?

Normally in a dual boot system this is enabled by default and you can choose from that menu which OS to use.  If you do not see this menu, and are using ubuntu 10.04, hold down shift after pressing the power button at start up and the menu may appear.  Give that a try as a start, and if it is not successful come back again and let's see where else we can go.

---

### Post by Arnoxsas on 2010-07-30
No i dont see grub meniu.

I have only one OS. Ubuntu 10.04, i want to change it into the windows. Amm. There is that power button? oh, is this then im turning on my computer?

---

### Post by ajgreeny on 2010-07-30
So you need to install windows; you should have said that you don't already have it, as I assumed you had a dual boot system, but could not boot into windows.

You will need to shrink your ubuntu partition using gparted on the ubuntu live CD to make space for windows, leaving the space unformatted.  Then when you install windows the CD should find that unallocated space and be able to install into it.  You will then need to restore grub and update it so that it will show both OSs when you boot.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Arnoxsas on 2010-07-30
Im just see Press F11 to Boot meniu, and etc.. 
If you talking about that button, it still not working.

---

### Post by Arnoxsas on 2010-07-30
No no no, sorry for mistakes. I want delete linux and install windows. I want only have one OS in my computer

---

### Post by soldier1st on 2010-07-30
if you only want windows then boot the livecd and access gparted from system/administration and delete and format the drive where ubuntu is installed then boot with the windows cd to start it's install but may i ask why do you want Windows only and not stick to Linux.

---

### Post by Arnoxsas on 2010-07-30
Look witch is faster on my computer.

---

### Post by Arnoxsas on 2010-07-30
I just want to boot windows cd, but i dont know how.. Because keyboard not working, F11, F2, Shift, ESC, R,Del. Nothing. I want to know how can i delete linux somehow from computer, and install windows.

---

### Post by ajgreeny on 2010-07-30
You need to get rid of ubuntu from the the hard disk first by booting to the ubuntu Live CD, starting gparted and deleting the ubuntu partitions, if you really want to get rid of it completely.

You will need to set the CD as first boot device in your BIOS to get the Live CD to run, and once you have a disk of unallocated space the windows CD should boot and find that space and be able to install to it without a problem.  At the moment windows is not clever enough to see a disk with a linux file system on it, so you can not simply install windows over ubuntu without removing ubuntu first.

---

### Post by Arnoxsas on 2010-07-30
i dont know how to install gparted.

---

### Post by soldier1st on 2010-07-30
Gparted comes with the LiveCD,the instructions i gave you will work.

---

### Post by Arnoxsas on 2010-07-31
You dont understand, i cant boot from cd, because F11 not working, and F2 not working.. And i dont know why the not working..It happned first time for me.. Always worked fine, but then writing Press F2 to bios, Press F11 to boot, keyboard not working..

---

