---
title: "How to install Lubuntu on an already formatted partition?"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by rasti2 on 2014-05-27
I am relatively new to Linux and I have a computer with a new 500 GB Western Digital HDD. Since it didn't come with an OS, I decided to install Lubuntu now and Windows later. I had an Ubuntu LiveUSB flash drive which I used to access Gparted and format a smaller partition for Lubuntu. I selected ext4 as the file system. After that I used a LiveCD burnt a few minutes before to install Lubuntu 13.10. I selected the Install Lubuntu option and when I came to the screen that offers you choice to either install alongside another OS, erase disk and install Lubuntu or use something else, I stopped. I wasn't sure which one to choose as I am a beginner and probably shouldn't use the something else option and I don't know if the install alongside another OS will work. Could you help me solve this?

Specs:
Asus H61M-K
Intel Celeron G1620
2 GB of 1333 MHz DDR3 RAM
Integrated Intel HD Ivy Bridge graphics
CD-DVD RW optical drive
500 W power supply

Thank You.

---

### Post by Rex Bouwense on 2014-05-27
How many partitions do you have already?  You can only have a maximum of four primary partitions.  One can, however, be an extended partition which can be divided up into an almost unlimited of partitions.  Since you do not have an Operating System installed you must choose "do something else"  unless you want to install Lubuntu on the whole drive.  A typical dual boot will be half Windows and half Linux.  Can you post a screen shot of GParted showing your existing partitions?  That might make it easier to advise you how to proceed.

---

### Post by LastDino on 2014-05-27
If you want to dual boot Windows and Linux, you would generally need to install Windows first.

---

### Post by rasti2 on 2014-05-27
Well now I feel bad for posting this. I tried something else option and it didn't work the first time but when I tried it again it worked and it's now up and running. Thank you for the help though and I just have two primary partitions, one for Lubuntu and one for Windows later.

---

### Post by LastDino on 2014-05-27
> **rasti2 said:**
> Well now I feel bad for posting this. I tried something else option and it didn't work the first time but when I tried it again it worked and it's now up and running. Thank you for the help though and I just have two primary partitions, one for Lubuntu and one for Windows later.

Judging by this looks like you've no separate /home or data partition. I suggest you take backup when you try to install windows as it is likely that you will need to install Lubuntu second time or at least keep that bootable Lubuntu around ;)

---

### Post by Rex Bouwense on 2014-05-27
When you decide to install Windows here is a little information.  LastDino is quite correct.  You should probably creat a separate /home for your data because while Lubuntu will read an NTSF file, Windows will not be able to read an Ext4 file.  Also see
[http://ubuntuforums.org/showthread.php?t=1389558](http://ubuntuforums.org/showthread.php?t=1389558)
It is an old thread but the information is valid.

---

