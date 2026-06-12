---
title: "Cannot mount / during install"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Dynamite on 2006-07-06
Hi everyone, I'm trying to install Ubuntu 6.06 on my PC from the alternate CD (not the graphical one) but I can't get past the partitioning step in the installation. 
After partitionnig my blank HD the installation shows an error message something like "Couldn't mount / root file system" and states that I have to go back to partitioning. 
The HD partitions look like this:
/root: 25 GB
/home: 173 GB
/swap: 2 GB

I've been trying all day to install ubuntu so I thought I'd ask for help, My PC Specs are as followed:
1- CPU: Intel Pentium 4, 3.4 GHZ HT.
2- Memory: 2 x 512 MB RAM (Total 1024 MB Ram I checked the ram with MemTest they are OK!).
3- Motherboard: MSI 915P Combo.
4- HDs: The blank HD is connected to IDE1 (The primary IDE).
5- DVD-ROM: Asus connected to IDE2.

I think the problem is in the connection of the HD & DVD-ROM to the motherboard but I have another HD with XP on it which I didn't connect to the motherboard during the install (To prevent Data lose), The XP HD should be connected as a slave with the Ubuntu HD as master to IDE1 after I manage to install Ubuntu.

I tried a few suggestions that I found while searching the forums like disabling ACPI in the BIOS but it didn't work. I even tried to let the partitioner choose the partitioning layout but that didn't work either. Could someone help me? I really want to install Ubuntu asap. Thanks again.

---

### Post by lamego on 2006-07-06
You have a /root when you should have just a / as the mount point, that is what the installer is complaining about.
And you don't need to disconnect the Windows HD to prevent data loss as long you read the install instructions and don't do anything you don't understand.

---

### Post by Dynamite on 2006-07-06
[QUOTE=lamego]You have a /root when you should have just a / as the mount point, that is what the installer is complaining about.
And you don't need to disconnect the Windows HD to prevent data loss as long you read the install instructions and don't do anything you don't understand.[/QUOTE]

Thanks for your help I appreciate it but the mount point I've set is correct, it is /, The installation wizard complains about not being able to mount / after partitioning (during the installation). Sorry I wasn't clear about the error message. Any other suggestions?

---

### Post by Nunana on 2006-07-06
I had something like this in the past. What I did:
I removed all partitions (and saved it). Shut down my pc and took the power cable out.
Another time that was not enough. I used a systemrescue CD and used fdisk to remove all the partitions, save, power off, cable out.
And started again.
Both times succes.
I hope it will help for you too

---

### Post by Dynamite on 2006-07-06
[QUOTE=Nunana]I had something like this in the past. What I did:
I removed all partitions (and saved it). Shut down my pc and took the power cable out.
Another time that was not enough. I used a systemrescue CD and used fdisk to remove all the partitions, save, power off, cable out.
And started again.
Both times succes.
I hope it will help for you too[/QUOTE]

What power cable are you talking about? The HDs Power cable or the PCs entire power cable (The one connected to a power outlet) and for how long did you keep your PC without power? Thanks alot for your replys

---

### Post by Nunana on 2006-07-07
The power cables of your PC.
Some PC's hold setting/information unless you unplug them.
It is just to be sure.

---

### Post by Dynamite on 2006-07-07
> **Nunana said:**
> The power cables of your PC.
Some PC's hold setting/information unless you unplug them.
It is just to be sure.

Thanks for your help, i'll try what you suggested tonight when I return home. Thanks again

---

### Post by Dynamite on 2006-07-08
Sry for the double post. I think I've managed to pinpoint the problem. First of all Nunana's suggestion didn't work. The problem occurs during partitioning, 

The partitioner never manages to create the 3 partitions successfully so it cannot mount them. I think the problem is that my HD (which is a Western Digital 200 GB HD should have a free space of about 180 GB not 200 GB) but the partitioner thinks that the 200 GB are free and available.

I've tried many partitioners but they all fail, I've tried the systemrescuecd, the alternate ubuntu 6.06 partitioner and the Gparted partitioner on the Xubuntu live CD and they all failed. Any suggestions?

---

### Post by Nunana on 2006-07-09
It sound like a wrong Master Boot Record. I had one on a USB stick size 512MB and my computer found 30GB(!) free space. Silly me I wrote down the full MBR (512 bytes) of my hard disk to the USB stick, instead of 446 bytes.
this link gave me more information that time [http://www.geocities.com/rlcomp_1999/procedures/mbr.html](http://www.geocities.com/rlcomp_1999/procedures/mbr.html)
Later on I whiped out the MBR. Be sure that you fill in the right disk! You will loose everything of the disk unless you have a copy it.
The most common way is to boot to a DOS/Win95/Win98 boot floppy and run the command: fdisk /mbr
I used th dd statement because a Micro$oftboot doesn't see a USB-stick as a hard disk, ( MAKE SURE YOU HAVE THE RIGHT DISK behind of= ):
dd if=/dev/zero of=/dev/sda bs=512 count=1

I don't know if this will work. It's weird that your disk clames it is bigger than it is. I realy hopes this works for you because i ran out of ideas and knowledge.

good luck

---

### Post by Dynamite on 2006-07-11
> **Nunana said:**
> It sound like a wrong Master Boot Record. I had one on a USB stick size 512MB and my computer found 30GB(!) free space. Silly me I wrote down the full MBR (512 bytes) of my hard disk to the USB stick, instead of 446 bytes.
this link gave me more information that time [http://www.geocities.com/rlcomp_1999/procedures/mbr.html](http://www.geocities.com/rlcomp_1999/procedures/mbr.html)
Later on I whiped out the MBR. Be sure that you fill in the right disk! You will loose everything of the disk unless you have a copy it.
The most common way is to boot to a DOS/Win95/Win98 boot floppy and run the command: fdisk /mbr
I used th dd statement because a Micro$oftboot doesn't see a USB-stick as a hard disk, ( MAKE SURE YOU HAVE THE RIGHT DISK behind of= ):
dd if=/dev/zero of=/dev/sda bs=512 count=1

I don't know if this will work. It's weird that your disk clames it is bigger than it is. I realy hopes this works for you because i ran out of ideas and knowledge.

good luck

I tried partitioning from windows using partition magic it it worked wonderfully (the partitioning part) when I tried to install it hung (crashed) while installing the base system sayaing certain packages where corrupted! (I checked the CD's integrity twice and the installer says that it is valid, I also checked it while burning with Nero and It was fine). What should I do now?

What I've concluded this far is that I thin the problem is with how the HDs & DVD-rom are connected to the motherboard Maybe it can't read stuff from the CD causing meanless error? Anyone?

---

### Post by Dynamite on 2006-07-12
*Bump*

---

### Post by Dynamite on 2006-07-18
Help Please? :(

---

