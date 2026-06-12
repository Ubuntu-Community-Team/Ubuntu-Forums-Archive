---
title: "how i could install ubuntu 10.10 on free space with windows??"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by shokoup on 2010-11-19
I don't know why they made us suffer!! , i can't find the "installing into free space" option in the new Ubuntu 10.10. I have two partitions one for Windows 7, the other for my data and a 80 GB free space for Ubuntu.
I want to install ubunto on the free space i have how ?????????????  the older versions were very easy.

---

### Post by Elfy on 2010-11-19
Well I always make partitions in the partition editor of the livecd before I start the installer.

Create an extended - then logicals for swap and /

Start the installer - use the advanced/or manual option at the partition stage.

Edit the / partition and make the mountpoint /

---

### Post by Rubi1200 on 2010-11-19
Hi shokoup,
there have been changes to the installer in 10.10 that can, and will, affect you.

This thread discusses some of the problems that you definitely need to be aware of:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I suggest you make backups before you start and use the tools in Windows 7 to create a repair CD (just in case).

---

### Post by santosh83 on 2010-11-19
> **shokoup said:**
> I don't know why they made us suffer!! , i can't find the "installing into free space" option in the new Ubuntu 10.10. I have two partitions one for Windows 7, the other for my data and a 80 GB free space for Ubuntu.
I want to install ubunto on the free space i have how ?????????????  the older versions were very easy.

I may be wrong here, but wont the installer option "Install next to/adjacent to the other OS" (I don't remember the exact wording, but it was similar to this), do what you want?

If not, then it's very simple to choose to partition manually and convert your free space into two partitions, one for / and the other for swap.

---

### Post by Elfy on 2010-11-19
Nice link rubi1200 - ty :)

---

### Post by Rubi1200 on 2010-11-19
> **forestpiskie said:**
> Nice link rubi1200 - ty :)
You are more than welcome sir :)

I believe that our friend kansasnoob is working on trying to affect changes for the upcoming 11.04 version that will rectify some of the "issues" with the current version of Ubiquity.

---

### Post by shokoup on 2010-11-19
> **santosh83 said:**
> I may be wrong here, but wont the installer option "Install next to/adjacent to the other OS" (I don't remember the exact wording, but it was similar to this), do what you want?

If not, then it's very simple to choose to partition manually and convert your free space into two partitions, one for / and the other for swap.

what i want is keeping my windows (as it is) in its separate partition and installing UBUNTU in the free space i have. The option you mentioned is to install ubuntu adjacent to windows (in the free space of windows partition not the rest contiguous free space of the hard drive )

---

### Post by dino99 on 2010-11-19
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

