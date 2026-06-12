---
title: "am i safe? - dual booting with winXP and Ubuntu"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by Wesley on 2005-08-09
hi guys

been using Ubuntu for on VMWare for some time, i'd like to install Ubuntu on my main PC

using SATA WD 74GB Raptor, i believe that it'll be no problem to install Ubuntu on SATA drives as i've read on Ubuntu forum

at the moment there're 2 partitions

1 for XP (60isb GB)
2 for Vista (10ish GB)

wanna get rid of Vista and install Ubuntu in that partition.

how? i've never manually edit/choose which partition to use when installing Ubuntu as i usually choosed automatically (whole hard drive in VMWare)

but firstly i need to get rid of that rubbish boot menu made by Vista but how?

will be using GRUB boot loader?

will Norton Ghost/Acronis TrueImage make image of Ubuntu partition and restore them?

if i want to get of Ubuntu in the future, i'd just delete the partition with PQ PartitionMagic but will it also remove the GRUB loader as well?

cant think of anymore questions to ask

cheers  :)

---

### Post by PeP on 2005-08-09
> how? i've never manually edit/choose which partition to use when installing Ubuntu as i usually choosed automatically (whole hard drive in VMWare) 
the installer can get rid of one partition and put the root partition instead, you might also want to delete the partition and make two (one for swap) or more (also one for home?) 

from your previous installation, just keep the /home folder and things that are relevant eg (/var/www  if you had a web server ... it won't be really interesting to ghost the whole partition since it is a very different system (ou hare on a virtual x386 with a special network card and display ...).

grub will be the bootloader, at worst you will have to uncomment some lines in /boot/grub/menu.lst to add the windows partition.

For the vista boot menu I don't know.

---

### Post by teapot on 2005-08-10
[QUOTE=Wesley]
if i want to get of Ubuntu in the future, i'd just delete the partition with PQ PartitionMagic but will it also remove the GRUB loader as well?
[/QUOTE]

PartitionMagic will clear the boot (remove GRUB) if you want it to. But you might just want to leave it. After all, you're playing with different operating systems, and you might just keep doing it  :) 

I prefer Grub to BootMagic (PM's boot manager), btw.

---

