---
title: "Installing Hoary on HPT370 GRUB problems"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by PhilBritton on 2005-08-03
I'm trying to install Hoary on a Athlon 1.1GHz on a Asus KT7A motherboard which has a HPT370 controller. There are three hard drives on this controller lets call them A, B and C. A has windows XP on it and appears to the installation program as hdf1 B is the slave in this pair, had a previous installation of Fedora on it and is recognised as hdf2. The third disk, C, is formatted as NTFS amd appears as hdg1. (those ones and twos could be zeros and ones but you get the drift)

I go through the normal install and reformat the old linux partitions on disk B, the installation runs and I get asked at the end if I want to include Windows XP as a dual boot option. I answer yes and I tell it to install grub in the MBR of disk A ( I've done this a number of times with Red Hat, SuSe and Mandrak on this machine so it doesn't appear to be a grub problem that I'm having).

When the machine reboots I don't even get as far as a grub menu or prompt the machine just reboots itself from the part where the grpahic card is recognised. If I boot the system using smart boot manager and choose to boot from the windows disks XP boots and runs. If I choose to boot from the disk whereI installed Hoary I ge the same reboot seqeunce as above.

Anyone any ideas ? I've searched the these forums and the internet at large and the nearest I've came is some sort of hackery-pokery with boot sector segments which I think can't be the answer as grub works fine from other distributions,

cheers

Phil

---

### Post by amohanty on 2005-08-03
I think /boot needs to be on the primary master HDD (hd1 in your case) for grub to work. 

AM

---

### Post by PhilBritton on 2005-08-03
That can't be the answer as I've been running other distros with exactly the same partition/disk layout

Phil

---

### Post by amohanty on 2005-08-03
Can you boot off of a LIve cd and post your menu.lst?

Grub is a multi stage boot loader which means it needs to know where its other stages are. Your menu.lst might help.

AM

---

