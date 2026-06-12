---
title: "Fresh install"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2011-09-06
My mini laptop does not have a CD drive. How do I do fresh install of the latest Xubuntu, i.e. wipe out any previous installation and have just the Xubuntu? I can use a memory card and a USB drive.

Thanks.

---

### Post by Neutrosider on 2011-09-06
just make a boot-usb stick. you can make one either using the boot medium creator under linux or for example linux live usb creator (lili) under windows: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by haqking on 2011-09-06
> **dodgingspam said:**
> My mini laptop does not have a CD drive. How do I do fresh install of the latest Xubuntu, i.e. wipe out any previous installation and have just the Xubuntu? I can use a memory card and a USB drive.

Thanks.


See here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I am not familiar with xubuntu but i imagine process works the same but need xubuntu.iso instead.

Hope it helps

---

### Post by dodgingspam on 2011-09-06
OK, I was able to get a copy on my USB, but now i get a message that my HD is too small. Can first format my drive before installing? If yes, how?

---

### Post by dodgingspam on 2011-09-06
I have an outdated version of OS on my laptop, which has very little storage space left. I would like to do a clear install of Xubuntu. How do I remove all files, and previous installation before I can run a fresh install?

Thanks.

---

### Post by Hakunka-Matata on 2011-09-06
Hi, Welcome to the forum

Installing Xubuntu from a LiveCD/USB installation medium, you'll get the choice of partitioning the entire hard drive during installation.  That will wipe out everything and use the entire disk for your Xubuntu system.
you could also create your partitions ahead of time, using gparted in ubuntu. 
Boot to the LiveCD/USB
select "try Ubuntu without installing"
open a Terminal; ```
sudo gparted
```, go to it then.

---

### Post by dodgingspam on 2011-09-06
The only options I get are:

Live Mode
Install
File Integrity Check
Memory Test

I tried Live mode and it loaded Xubuntu but when I checked for OS info it was still showing Ubuntu 8.04.

When I ran Install it also never asked me how to install, but rather asked to pick a language, then calculated something for a while and presented with three items check, 

At least 4.4 Gb needed (fail)
Connected Power Source (pass)
Connected to Internet (fail)

I feel like I'm running in circles. Before I do it again, I thought I'd just use some line command and format the disk. I do not need anything on it! After that I can try to install.

---

### Post by azertyh on 2011-09-06
hello,
see the tutorial for installing ubuntu [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall). it may be a little different from what you see.
to use the entire HD, at step 5 of the tutorial, choose "erase disk and install ubuntu".

---

### Post by dodgingspam on 2011-09-06
Unfortunately I don't get past item#2. I need to free some room to install.

---

### Post by Hakunka-Matata on 2011-09-06
So what Operating System are you running on now?  Here, in the forums?

what do these give you?:
uname -a
sudo sfdisk -luM
sudo lshw -C display
free
df -h

---

### Post by dodgingspam on 2011-09-06
It's Ubuntu 

free gave me the following
----------
total: 
 Mem: 1024932
 buffer/cache:0
 Swap: 0

used:
 Mem: 80460
 buffer/cache: 32484
 Swap: 0

free:
 Mem: 944472
 buffer/cache: 992448
 Swap: 0

shared
 Mem: 0 

Buffers: 
 Mem: 3148

cached
 Mem: 44828


-------------
and df -h

Filesystem    Size   Used  Avail  Use%   Mounted on
------------------------------------------------
/dev/sda2     3.4G   2.0G  1.3G   61%    /
varrun        501M   56K   504M    1%    /var/run

and so on 0-1%

---

### Post by Hakunka-Matata on 2011-09-06
Ubuntu: 
Q:  what release?
A:



QYou are running LiveCD/USB or off disk?
A.  

please post output of sudo fdisk -lu

---

### Post by dodgingspam on 2011-09-06
Ubuntu 8.04.06

Trying to install from USB drive.

And I guess my current setup is pretty messed up. It loads as a command line prompt and produces no results when I try fdisk -lu

---

### Post by Hakunka-Matata on 2011-09-06
```
sudo fdisk -lu
```

---

### Post by dodgingspam on 2011-09-06
fdisk -lu
************
Disk /dev/sda: 3791 MB, 3791241216 bytes
128 heads, 63 sectors/track, 918 cylinders, total 7404768 sectors
Units = sectors 0f 1 * 512 = 512 bytes
Disk identifier: 0x80d78fd6


Device........Boot....Start.........End...............Blocks............Id.........System
/dev/sda1..............63............64511............32224+........de.........DellUtility
/dev/sda2...*.........64512......7394687........3665088......83..........Linux

Ignore dots -- I used them for spacing only

---

### Post by Hakunka-Matata on 2011-09-06
> **dodgingspam said:**
> fdisk -lu
************
Disk /dev/sda: 3791 MB, 3791241216 bytes
128 heads, 63 sectors/track, 918 cylinders, total 7404768 sectors
Units = sectors 0f 1 * 512 = 512 bytes
Disk identifier: 0x80d78fd6


Device........Boot....Start.........End...............Blocks............Id.........System
/dev/sda1..............63............64511............32224+........de.........DellUtility
/dev/sda2...*.........64512......7394687........3665088......83..........Linux

Ignore dots -- I used them for spacing only
Hard Disk of 3.8 GB, 
The hard drive size makes it difficult to work with.  It' quite small.

---

### Post by dodgingspam on 2011-09-06
I know. Is there a way to reformat the drive and install Xubuntu from USB?

---

### Post by Hakunka-Matata on 2011-09-06
I guess so, especially if you don't need to save any important data off your hard drive before reformatting it.

Just install your Xubuntu, tell it to use the entire hard disk.  No?

---

### Post by dodgingspam on 2011-09-06
I can not install it because I don't have enough room. Is there a utility or a command that I can use to wipe the drive clean and install fresh? I tried rm but apparently I do no have adequate permissions... Windows has "format" command, doesn't Linux have something similar?

---

### Post by Hakunka-Matata on 2011-09-06
System>Administration>gparted or partition manager

---

### Post by dodgingspam on 2011-09-07
I tried gparted from Live boot but it just keeps spinning and shows no results. Is there a line command?

---

### Post by Hakunka-Matata on 2011-09-07
```
sudo sfdisk
```

---

