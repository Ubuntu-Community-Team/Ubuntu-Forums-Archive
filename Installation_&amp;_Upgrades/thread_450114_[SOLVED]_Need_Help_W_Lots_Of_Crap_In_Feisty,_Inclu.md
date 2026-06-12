---
title: "[SOLVED] Need Help W/ Lots Of Crap In Feisty, Including Partitioning!"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by pHreaksYcle on 2007-05-21
This is going to be long whether I like it or not, so I will TRY to keep it short...thanks for your time in advance whoever is brave enough to help! (and yes, I did try Google for all this stuff first!) Any questions about this, please respond here or to dknoll {[at]} sjci DOT (((COM)))

I am using a:
Dell Inspiron 1501 LAPTOP (WXGA wide screen)
AMD Turion 65 (2.0GHz/512KB)
80GB Hdrive
ATI RADEON Xpress1150 w/ 256MB of RAM
Came with Image Restore on Disk
Windows Version=Vista

Have Intermediate to Advanced knowledge across the board. I know lots of stuff, but have little things missing here and there. (That is what G00gle is for right?)

I installed Ubuntu Feisty Fawn, using it for school for about one month/month and half, works great for taking notes etc. One problem, NO WiFi, just wired, which=pain in ****. No matter what I do, no matter how many guides I follow, programs/firmwares I install (ie: ndiswrapper) it just wouldn't work. (Still doesn't)

I also wanted to get Beryl to work. No good there either, followed all of the steps, tried every guide I could follow, nothing.

I have been using this site [http://www.ubuntu1501.blogger.com](http://www.ubuntu1501.blogger.com)
and it's guides, no good. (Did mail out for the free sticker though!)

My question is how to get WiFi working and Beryl or Compiz or whatever the hell it is! The jigglyz and the desktop cube! That is all I ask!

IN ADDITION, to these problems, while trying to get these two problems to work, WiFi and Beryl (jigglyz ), I installed Uberyl. This is a not-very-known Spanish distro and it is supposed to have Beryl and WiFi on laptops working "out-of-the-box". (Or off the CD I suppose...) Needless to say, since I am posting this, none of this crap worked! Trying countless re-installs of Feisty and Uberyl (which is Ubuntu version Edgy), and not knowing ANYTHING about partitioning except where Windows is located, I have ended up with FOUR OS's ON MY LAPTOP! That is a secondary issue, but one I would like to take care of if possible. I do not want to screw up my Vista installation, but if that is part of someones grand scheme to make these things work, I'm down! I have no qualms about wiping the slate clean if that is what it will take and I have instructions on how. I am trying to at least wipe all Ubuntu from my system and start over with just Vista.

BTW, this is the output from GRUB on boot-up if it helps (or even if it doesn't, I guess...)

Ubuntu Kernel 2.6.20-15-generic
"SAME THING" recovery mode
then the Ubuntu memtest option
Other:
M$ Vista (loader)
Ubuntu 2.6.17-11-generic (on /dev/sda5)
Ubuntu 2.6.17-11-generic revovery mode on (/dev/sda5)
Ubuntu 2.6.17-10-generic (on /dev/sda5)
then the Ubuntu memtest option.

I assume the -10 is Uberyl because Uberyl is Edgy and that is an older verions which=older number...
Sorry if I rambled a little bit, but it's late and I am strung out about this.
I would like to stay with Linux (specifically Ubuntu, cuz it has a very strong community it seems), but this is starting to discourage me lots... Thanks SO MUCH for your help in advance if any is available!!!

---

### Post by mikewhatever on 2007-05-21
What a mess! Can you post this from the terminal
> sudo fdisk -l

I think you need to slow down. Beryl is only a flashy windows manager, and it's not gonna go away. Also, keep in mind, that it is still in beta. By the way, the link you posted does not work.

What wireless card do you have? Can you post the output of this
> sudo lshw -C network

---

### Post by pHreaksYcle on 2007-05-21
Lemme boot in Ubuntu and I will edit this post when I am back!
Okay, back! Sadly, after this I have to call it a night! It is about 2AM and I have school today, so we must pick this up later AKA 2moro. Here are the outputs of sudo fdisk -l and sudo lshw -C network respectively

CODE:
dan@dan-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        4536    36363127+   7  HPFS/NTFS
/dev/sda3            9124        9729     4867695   db  CP/M / CTOS / ...
/dev/sda4            4537        9123    36845077+   5  Extended
/dev/sda5            6254        8998    22049181   83  Linux
/dev/sda6            8999        9123     1004031   82  Linux swap / Solaris
/dev/sda7   *        4537        6175    13165204+  83  Linux
/dev/sda8            6176        6253      626503+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 130 MB, 130023424 bytes
16 heads, 32 sectors/track, 496 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         496      126960    6  FAT16

CODE:
dan@dan-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7d:14:33:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0203fff irq:18
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c8:be:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:c0300000-c0301fff irq:21

Thanks for your help so far and hope to hear from you tomorrow in between classes! (Same laptop, have it glued to me half the day!)

---

### Post by pHreaksYcle on 2007-05-21
Also, that link was ubuntu1501.blogSPOT.com not blogger...the page is neat, made by a guy with same laptop as me and ONLY does stuff about that laptop running Ubuntu. Frequently problematic things with that specific PC is on that page and it's handy....later!

---

### Post by mikewhatever on 2007-05-21
Since you really seem to have two linux installations, I'd suggest deleting the following partitions:
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda8
and starting over by reinstalling Feisty. You'd be better off by finding a different guide to Beryl & ATI. Look here for example [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Your wireless is a broadcom 4310. It might work, but usually needs work to set up
[http://ubuntuforums.org/search.php?searchid=20573466](http://ubuntuforums.org/search.php?searchid=20573466)

Have a good night.

---

