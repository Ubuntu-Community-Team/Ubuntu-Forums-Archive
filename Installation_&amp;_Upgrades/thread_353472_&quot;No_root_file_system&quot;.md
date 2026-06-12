---
title: "&quot;No root file system&quot;"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Orta on 2007-02-04
Today I came up with a problem during my Ubuntu install. During installation, I got a "No root file system" error. Here is what I did from the beginning:

Steps taken
1- Created ext2 and swap partitions using Partition Magic 8.01 under Windows XP. Tried ext3 before but it did not solve the problem either.
2- Put the Ubuntu 6.10 cd in the drive and restarted the computer.
3- When the menu popped up, I hit F3 and selected Portugal (because of my keyboard). Then, to "override" the "problem" X has with ATi cards (mine being X700 Mobility), I removed the "quiet splash" command using the F6 option (and backspace :-P) and hit Enter. 
4- I waited for X to return the "Failed to start the X server yada yada..." error and then went back to the command line.
5- sudo nano /etc/X11/xorg.conf, changing "ati" to "vesa" in order to use the graphical installer. Please note that the plan is to install fglrx later on.
6- startx.
7- The desktop appears. "Install".
8- During the installation process, on step 5, I get a "No root file system" error:

[[IMG]http://img292.imageshack.us/img292/9562/screenshotuc9.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshotuc9.png)

I found a workaround here on the forum ([http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29) ), but I fear it might destroy my Windows partition which is out of the question (you know the hell of Windows reinstallation...).

What can I do? Many thanks.

PS: laptop specs - Pentium M 750 1.86GHz, 1GB RAM, 80GB SATA HD which worked very well with 6.06 before I decided to format it completely... ](*,)

---

### Post by Rui Pais on 2007-02-04
hi,

i think you should avoid following that tip. Sounds like a dirty workaround to make some buggy rc version to install...

The problem probably is here:
> **Orta said:**
> 1- Created ext2 and swap partitions using Partition Magic 8.01 under Windows XP. Tried ext3 before but it did not solve the problem either.

Partition magic did something that the installer don't like (or even forget to format the new made partitions). It's a windows tool that you don't need to install a Linux. Have  you tried reformat the partition launching gparted from a terminal before runing the installer. Or simply remove the partition and leave the space empty, choosing 'Install on free space' option...

Anyway don't install on an ext2! Thats bad, you will loose journaling system. At first failure  you will loose data or compromise the integrity of system.

Boa sorte.

---

### Post by Orta on 2007-02-04
Downloading updates right now, all went all. Thank you very much. Or should I say "muito obrigado"? ;)

Just a small note, I used Partition Magic to delete the created ext2 and swap. Then I did as you instructed, selecting that "free space" option. Thanks!

---

### Post by Rui Pais on 2007-02-04
he he, de nada :)

have fun

---

