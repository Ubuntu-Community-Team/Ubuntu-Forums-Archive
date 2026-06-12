---
title: "[SOLVED] Xubuntu installation problem"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by antoant on 2007-08-09
I am trying to install Xubuntu (Feisty Fawn) on my old Dell Optiplex GX150. After I choose the Install Xubuntu option from the first menu I get a pop saying Loading Kernel that goes to 100%. Then I get a screen with the Xubuntu logo and a small bar moving left and right in a Windows fashion. After that happens for a minute or two I start getting the following.

[number that keeps changing] ata1.01: exception Emask 0x0 SAct ........
... BMDMA stat 0x64 ...
Buffer I/O error on device sda1, logical block 32
Buffer I/O error on device sda1, logical block 33
Buffer I/O error on device sda1, logical block 34
Buffer I/O error on device sda1, logical block 35

These lines keep repeating with the first two lines appearing a few times before the rest of the lines appear again.

I tried using another CD-ROM device from another computer on which I manage to get the live CD to boot.
I tried taking out one of my two sticks of RAM as was suggested in another thread.

I tried to check the CD for errors but I get the same error as above. (The CD check requires the live CD to boot????)

Can anyone offer any help?

PC Specs:

P3 1.15Ghz
256 MB RAM

---

### Post by Pumalite on 2007-08-09
I advise you to use Alternate Xubuntu CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Take a look at this too: [http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345)

---

### Post by antoant on 2007-08-10
I left my computer on for the night and it appears that the live CD finally loads. I tried the alternate CD too, just to be sure, and I get the same errors. So it must be some sort of problem with my hardware. Maybe the the ide drivers??? Has anyone observed this problem before?

---

### Post by Pumalite on 2007-08-10
Mobo, graphics, chipset?

---

### Post by antoant on 2007-08-10
The mobo is made by foxconn. However, as I said originally the pc is a Dell so I believe it was designed specifically for dell. I am using the on-board graphics card. The chipset is the Intel 815.

---

### Post by antoant on 2007-08-14
It seems that one of the disks I was using has something wrong with it and it was causing problems. As I wrote before I could load live CD after waiting for awhile. I installed xubuntu and kept getting the errors that I reported before. So I just unplugged the second hard disk (sdb) and the errors went away. I will open another thread about that problem. Thank you for your responses Pumalite.

---

