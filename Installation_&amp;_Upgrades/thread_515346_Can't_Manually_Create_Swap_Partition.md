---
title: "Can't Manually Create Swap Partition"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by Otus on 2007-08-01
I am attempting to build a dual boot XP / Ubuntu 7.04 ThinkPad t40. The machine had 7.04 installed and running since the 7.04 release. I now have a need to use Windows every once in a while and decided to rebuild the hard drive to support all this madness. The machine has a  120 gig hard drive and 1 gig of RAM.

I have successfully installed XP in a 20 gig partition and tried to install Ubuntu 7.04 with the following partition design:
[LIST]
[*]20 gig partition for the "/" mount point
[*]2 gig partition for /swap
[*]The remainder of the hard drive for /home
[/LIST]

And, finally, here's the problem. When I step through the installer's manual partitioning process I can create the 20 gig boot partition but when I try to define the swap partition I cannot select "/swap" from the mount point drop-down list. I can type /swap in the associated text box and continue defining partitions. And I can define the /home partition. When I try to advance to the next step in the installation the installer tells me that I have not defined a /swap partition. Any suggestions regarding what's going on with the installer? Thanks in advance for any help and suggestions.

---

### Post by Pumalite on 2007-08-01
You could try Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and prepare your partitions before the installation. This Gparted is better than the one that comes with the installation disk. It's a small download that you burn to a CD. Then you boot this CD and you are in business.

---

### Post by kevinlyfellow on 2007-08-01
If you have enough ram, you could even 
```
sudo apt-get install gparted
```
while running the livecd.

---

