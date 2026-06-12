---
title: "installation on existing partition"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by kitts on 2006-04-19
i already have 4 primary partitions on my 40gb drive. i left 6gb of one partition 'raw' without any file system. Now when i start installation from the ubuntu cd..the installer starts some 'partition manager ' and asks to partition my hardrive. I want to install ubuntu on the partition (raw)existing.
         how can i skip this partition manager and install ubuntu on my raw drive(with whatever file system ubuntu supports)?:confused: :o

---

### Post by uantuzri on 2006-04-19
It is necesary to run the partition manager to gonfigure them, but that doesn't mean that you have to make more partitions. 

You have some information here :

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

Remember that you need a swap partition!

---

### Post by kitts on 2006-04-19
Help me..the installer failed installing "base system" Why?
My Manual partition settings are like this.
The partition i selcted is 6.9Gb.   Filesytem:  fat32 
                                             Mountpoint: /     --->as suggested in help
                                           bootflags    :  default
I went ahead without swap space..as i thought there is no need for it when i got 7gb of which the ubuntu takes only 2gb.

Lucky ..i always keep my Reatogo winxp live cd while expermenting these things. It changed the active partition to non-windows drive. i changed it back to my system drive.

---

### Post by uantuzri on 2006-04-19
To make Linux work you need an ext2 or ext3 filesystem, that why it fails.

When I install Ubuntu, I try having a 10GB partition. I read somewere that you don't really need 10, 6 were enough, but sometimes the installation fails if you don't have 10. I don't know if it is really necesary, but everything should work with those 6.9GB.

I'm not quite sure about that on the swap partition, specially if you don't have  plenty of extra space on your hard disk. 256Mb or 128Mb should be enough though.

Anyway, try changing the filesystem to complete the installation.

Good luck.

---

### Post by kitts on 2006-04-19
[QUOTE=uantuzri]To make Linux work you need an ext2 or ext3 filesystem, that why it fails.

When I install Ubuntu, I try having a 10GB partition. I read somewere that you don't really need 10, 6 were enough, but sometimes the installation fails if you don't have 10. I don't know if it is really necesary, but everything should work with those 6.9GB.

I'm not quite sure about that on the swap partition, specially if you don't have  plenty of extra space on your hard disk. 256Mb or 128Mb should be enough though.

Anyway, try changing the filesystem to complete the installation.

Good luck.[/QUOTE]
**Thanks the problem was the filesytem as u said should be ext2 or 3.** the installation finished smoothly. I am posting from my firefox on Ubuntu. i can boot winxp and Ubuntu smoothly. Ubuntu is running quiet good.:p :) :D

---

### Post by uantuzri on 2006-04-19
hey! good then. Wellcome to the Ubuntu world.

Now, you just have to update and personalice it (thats the best part of all)

---

### Post by kitts on 2006-04-19
[QUOTE=uantuzri]hey! good then. Wellcome to the Ubuntu world.

Now, you just have to update and personalice it (thats the best part of all)[/QUOTE]
Update? How do i do that? Sorry, i sometimes find it dificult to search all the forum and wiki.

---

### Post by Sef on 2006-04-19
> Update? How do i do that? Sorry, i sometimes find it dificult to search all the forum and wiki.

Applications > Accessories > Terminal

sudo apt-get update  

sudo apt-get upgrade

---

### Post by kitts on 2006-04-20
[QUOTE=Sef]Applications > Accessories > Terminal

sudo apt-get update  

sudo apt-get upgrade[/QUOTE]
it say o upgraded, 0 newly installed,0 to remove and 0 not upgraded..

Does it mean there are no updates?

---

### Post by uantuzri on 2006-04-20
[QUOTE=kitts]it say o upgraded, 0 newly installed,0 to remove and 0 not upgraded..

Does it mean there are no updates?[/QUOTE]

This means that youre system is updated. You don't have to worry much about looking for the updates, an icon will appear on the system tray, next to the time and date telling you that there are new updates available.

If you don't know where to begin looking for info, try this:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by kitts on 2006-04-20
Applications installations:
                 i tried some old verison of Yahoo mesenger 1.0.4.1.deb ..
                               it asks for more and more packages before it can be installed..
list of  packages i couldn't install 
> root@kitts:~/Desktop# dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 57492 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

       in total i downlaoded some 6 packages after google search and i still can't install yahoo messenger?
Myth Tv:      'apt get install <apache or mysql etcc.> ' says no such packages found ..it neither downloads from any link..read couple guides..but the installation s seems to be very tedious procedure of 30 minutes.

---

