---
title: "Installing UBUNTUon second HD, having WINDOWS on first HD"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by tucano on 2007-09-17
Hi there! this is my first post!


I have a question I didn't solved searching with google or in the forum:

I would like to have dual boot with WINDOWS on my first HD and UBUNTU on my second one: both HD are 

internal, the Windows HD ( hda ) is 114 GB and the Ubuntu ( hdb ) is 80 GB.

The question is: if in the BIOS the bootable hd is "hda" and I install Ubu on "hdb" where do I have to place 

the boot partition?Which procedure do I have to follow?

 I'd like to have a real dual boot, without having to change the HD for boot in the BIOS 

every time to switch between the systems.

---

### Post by olieviya on 2007-09-17
This should be pretty straight forward even for newbies.

Install windows first (always) and then install Linux, Ubuntu sorts everything out to boot perfectly and will create a menu to choose which OS you want from GRUB.

---

### Post by tucano on 2007-09-17
I know this things, but my doubt was: the grub boot partition has to be installed on the hd0 or on the hd1?

( i think hd0 is the primary boot HD (win) and hd1 is Ubu disk).

I think I have to install grub on the boot disk right? so on hd0.... And after installed do I have to edit some 

files or grub recognizes automatically that I have win on the first HD and Ubu on the second?

Thanx for answers!

---

### Post by ddrichardson on 2007-09-17
Grub can be installed wherever you want it to. If you use hda then it will be on the master boot record for the first drive and should pickup Windows during installation. If it doesn't then it can be added.

---

### Post by tucano on 2007-09-17
ok, so I will try to install Ubu with grub on hd0, equal to hda, and then the Ubu system on hdb...I'll post the resul of the operation.

---

### Post by ddrichardson on 2007-09-17
Make sure you backup first.

---

### Post by debianchick on 2007-09-17
> **tucano said:**
> Hi there! this is my first post!


I have a question I didn't solved searching with google or in the forum:

I would like to have dual boot with WINDOWS on my first HD and UBUNTU on my second one: both HD are 

internal, the Windows HD ( hda ) is 114 GB and the Ubuntu ( hdb ) is 80 GB.

The question is: if in the BIOS the bootable hd is "hda" and I install Ubu on "hdb" where do I have to place 

the boot partition?Which procedure do I have to follow?

 I'd like to have a real dual boot, without having to change the HD for boot in the BIOS 

every time to switch between the systems.

You don't have to change the HD every time you want to switch between Windows and Ubuntu. Installing Linux is easier than installing Windows. Ubuntu and other distros can be installed on any drive you want and all distros comes with a boot manager called Grub. Just choose the default options during the install and after you will be asked where you would like grub installed. Choose the default to have it install in the MBR on first HD and it will also add a entry into NTLoader Windows boot manager

---

### Post by tucano on 2007-09-17
> Just choose the default options during the install and after you will be asked where you would like grub installed. Choose the default to have it install in the MBR on first HD and it will also add a entry into NTLoader Windows boot manager

ok thank you, this is exactely what I wanted to know.. 

I wanted to be sure before trying the installation process. I installed linux many times (suse) but always on different partitions of the same HD, so I have never had the doubt of where to locate grub partition.

Thanx again, I will post after the installation!:popcorn:

---

### Post by Peter6218 on 2007-09-17
> **debianchick said:**
> You don't have to change the HD every time you want to switch between Windows and Ubuntu. Installing Linux is easier than installing Windows. Ubuntu and other distros can be **installed on any drive you want** and all distros comes with a boot manager called Grub. Just choose the default options during the install and after you will be asked where you would like grub installed. Choose the default to have it install in the MBR on first HD and it will also add a entry into NTLoader Windows boot manager

Actually it can't!! I tried yesterday to install to an HD on a RAID card. Won't do it!!

---

### Post by tucano on 2007-09-18
I WAS ABLE to install from live CD ubuntu 7.04:

Win is on hda (also recognized as hd0)

UBU is on hdb (also recognized as hd1)

hd0 is the hard disk which is designed as the boot disk in the BIOS

I installed Ubu on hdb, leaving grub boot partition to hd0 (default option).

So, now the situation is: I boot the PC from my standard HD, the windows one (i didn't need to touch BIOS), grub recognized my win O.S. and added it correctly in /boot/grub/menu.lst

Everything ok for me....Thank U! For any question ask by PM \\:D/

---

