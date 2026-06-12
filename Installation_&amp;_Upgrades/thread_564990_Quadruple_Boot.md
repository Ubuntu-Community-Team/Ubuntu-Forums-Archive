---
title: "Quadruple Boot"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by rafaelxy on 2007-10-01
I have been using ubuntu for a while, but now I want to check out others distros and new stuff.

I want to make a quad boot and was wondering how is the best and easier way to do it. I need windows xp sp2 obviously, for graphical work and Adobe CS3 usage (maybe use mac osx, but I'm on a pc and dont know if it will fit well), and want to install also Ubuntu 7.04, Gentoo 2007 and FreeBSD.

Any hints? Which one should I install first? How I gonna partition the HD? should I make a exclusive partition for /boot/? Please help me, Im not an dumb geek, but Im quite newbie in unix-like OSes.

---

### Post by rsambuca on 2007-10-01
Partition your drive in advance, so you don't have to worry about the partitioner screwing things up later.  Always install Windows first, the rest don't matter.  You don't need a separate /boot partition by any means (I have seven OS's and just use the Ubuntu grub).

---

### Post by rafaelxy on 2007-10-01
What exacly mean "partition your drive in advance"?

I gonna format 100% of the HD in NTFS when installing WindowsXP? And after that? Resized it with qt-parted?

---

### Post by rsambuca on 2007-10-01
> **rafaelxy said:**
> What exacly mean "partition your drive in advance"?

I gonna format 100% of the HD in NTFS when installing WindowsXP? And after that? Resized it with qt-parted?

If you are starting all of the OS's from scratch, then I recommend partitioning the drive before installing anything.  I have no idea what size your drive is, but as an example, say you have a 100GB drive, and you want 20GB for each OS plus 20GB for shared media.  Then you would use gparted to create the partitions before hand, and then install XP to the first 20GB partition.  Then install a linux distro, then another.  

Windows should be on the first primary partition, and the rest can be in logical partitions in one big extended partition if you like, and they can all share a swap.

---

### Post by rafaelxy on 2007-10-02
Cool! Im thinking of using the partition manager from ubuntu alternate install cd, that i can make the partitions and abort to install windows first! Is that possible?

Can really ubuntu and other unix-like be installed in logical partitions?

What's the advantage of using the /boot partition?

---

### Post by floke on 2007-10-02
Setup XP then resize and partition after.
You'll make 3 primary partitions - then 1 extended - which can be subdivided as much as you like.
You'll need to make 1 swap partition (all Linux can share it).

I have 

(1) Primary = Linux Mint
(2) Primary = Ubuntu
(3) Primary = Debian
(4) Extended -- -- --
(5) -- Logical = Arch
(6) -- Logical = general ext3 partition for storing documents etc. that all OS' can access
(7) -- Logical = swap

Just plan the sizes first!

---

### Post by rsambuca on 2007-10-02
> **floke said:**
> Setup XP then resize and partition after.
You'll make 3 primary partitions - then 1 extended - which can be subdivided as much as you like.
You'll need to make 1 swap partition (all Linux can share it).

I have 

(1) Primary = Linux Mint
(2) Primary = Ubuntu
(3) Primary = Debian
(4) Extended -- -- --
(5) -- Logical = Arch
(6) -- Logical = general ext3 partition for storing documents etc. that all OS' can access
(7) -- Logical = swap

Just plan the sizes first!

It doesn't make any sense at all to resize AFTER installing XP.  If you know ahead of time what you want to do, then partition first and then install everything.  Errors caused from resizing and partitioning are fairly rare, but why do it if you don't have to?

---

