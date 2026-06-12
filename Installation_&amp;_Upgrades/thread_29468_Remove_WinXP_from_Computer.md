---
title: "Remove WinXP from Computer"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by impman89 on 2005-04-24
Right now i have an XP/Ubuntu dual boot and i think i'm ready to completely scrap XP. My harddrive partitions are as follows (80GB):

WinXP 20GB NTFS --- Ubuntu 20GB Ext3 --- Shared Files 40GB Fat32


What i want to do is get rid of xp, convert the shared files partition to ext3 and mount it as /home. I want to have 20GB ext3 for / and 60GB for /home.

What is the best way to go about this? And any suggestions are welcome

---

### Post by derrick1985 on 2005-04-24
[QUOTE=impman89]Right now i have an XP/Ubuntu dual boot and i think i'm ready to completely scrap XP. My harddrive partitions are as follows (80GB):

WinXP 20GB NTFS --- Ubuntu 20GB Ext3 --- Shared Files 40GB Fat32


What i want to do is get rid of xp, convert the shared files partition to ext3 and mount it as /home. I want to have 20GB ext3 for / and 60GB for /home.

What is the best way to go about this? And any suggestions are welcome[/QUOTE]

Hmm.... that's a tricky one. I would probably get a copy of GNUparted (I think you can get it through apt) and format the NTFS partition ext3. After that, i'm unsure. I don't know exactly how well Linux would like another partition added to it's preexisting one. I know with Partition Magic for Windows, it adds the contects as a folder on the main drive.

As well, i don't think you can add it to home, unless you have a home partition already made up! you might just have to add it to your existing ext3 partition. And first of all, make a backup of both your files (windows and Linux) just in case something goes wrong. 

Another good program to try is qt_parted, that's the one i've used on the Mepis CD to make my linux partitons. You can get both on a BootCD from [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by gunnyman on 2005-04-24
I did this very thing except I turned my old XP partition into a /data
install gparted, nuke the NTFS partition, make a new one.
You can move your existing /home but it's a bit more involved than I feel competent to explain.
I just have symlinks to my mp3's and pictures in /home that link to my 160 gig data partition.

---

### Post by nad on 2005-04-24
impman,

I will respond to this later with full instructions. It has been a little hectic today. I do not want to rush as some of the changes you wish are tricky, and wish to be clear to a new user.

---

### Post by impman89 on 2005-04-24
thank you very much nad

---

### Post by nad on 2005-04-25
Okay. I have a plan. I've scrapped my draft idea about doing it the system administrators way. We'll do it the geek way. It's actually more certain and allows us a couple of check points.

First we need some information and tools. Please post the output of the command: df -hl

and the file hda.txt output by this command: parted /dev/hda print > hda.txt

Now the tools. You will need a live cd version of linux. If you have an ubuntu live cd, that will work. If not and you have a highspeed connection and the ability to burn an iso file, go to [www.knoppix.org](www.knoppix.org) and download the file (almost 700M!). Or you could try something smaller: [http://salvare.sourceforge.net/downloads.php](http://salvare.sourceforge.net/downloads.php) (~20M).

I await your reply.

---

### Post by impman89 on 2005-04-25
thanks for all the help guys, i figured it out myself.

---

