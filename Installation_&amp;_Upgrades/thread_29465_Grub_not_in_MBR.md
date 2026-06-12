---
title: "Grub not in MBR"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by KAMI no kodomo on 2005-04-24
I don't whant grub or lilo or stuf like that in my MBR. I want that commes in my pbs (partition boot sector). So i just have to set the 'grub' partition acive to have my grub loaded but when i set an onter partition active i will by-pass my grub. Is there anny whay to do that when i install ubuntu or is it realy impossible to not getting grub in my mbr?

---

### Post by nad on 2005-04-24
Until the ntfs pbr supports booting multiple operating systems of the users choice, you are stuck with the requirement of having to use another bootloader. Ubuntu uses grub, however lilo will also work. There are other bootloaders available also that I am not familiar with.

The concept of an active partition is indigenous to mostly microsoft operating systems. Linux ignores the boot flag as does your systems' bios. Whatever device you choose to boot from in your bios will be searched for a bootloader in its first sector.

---

### Post by KAMI no kodomo on 2005-04-25
I know what grub dus. I alraidy have it on my laptop (currently i'm using Fedora but want to change to some easy debian based Linux) Bit currently in boot sector of my Fedora partition (ext3) i have installed grub. And i setted in my mbr that partition active. So my bios looks in my mbr, goos tho the ext3 partition, reads there in my pbs the start of grub and loads grub (works parfect). En when i format my windows (somting usual) i'm sure the maximum troubels i have is that i afterwards have to set once again my ext3 partition as active and i never lose my grub (even when i lose my mbr)

---

### Post by nad on 2005-04-25
Ah. I understand your question now. And to tell you the truth, I'm not certain that the ubuntu install gives a location option regarding grub. I did so many installs last week that my memory fails me.

I do recall that ubuntu is not a straight debian install and that it seemed a little quirky. I also recall an issue, installing hoary, where grub was not installed where I thought that it should have been. I am just so use to configuring systems once they are installed that a little issue like grub is handled without thought.

Sorry I can't be of more help. I know that there are several message threads here regarding grub issues. The ubuntu installer definitely needs a little work.

My suggestion is to backup your current /boot partition and do the ubuntu install. If you have problems you will know where to find your good files.

---

