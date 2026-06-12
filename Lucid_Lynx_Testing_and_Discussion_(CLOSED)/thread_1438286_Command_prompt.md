---
title: "Command prompt"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by oscarrodas on 2010-03-24
Hi there, I got a question, I installed ubuntu 10.4 alongside windows 7, erevything when really smooth until came time to reboot; I get presented with two options the first one is windows 7 which boots ok, but the second option says Ubuntu, if I select it I get a command prompt, I really don't know what to do after that, not very literate on commands, all I can say is that during the installation I remember it said that it was installing as a superuser, any help will be appreciated, thank you. I have tried my user name and password but it says unknown command.

---

### Post by oscarrodas on 2010-03-24
Hi, after reading other post I tried the command exit and get the following: "PXE-EC8: !PXE structure not found in UNDI driver code segment.
PXE-M0F: Exiting PXE ROM
Operating system not found."
I have checked my bios and disabled Network booting but it doesn't make any difference Network Booting enabled or disabled doesn't make any difference.
The other command I saw is startx but it doesnt make anything.

---

### Post by uRock on 2010-03-24
When you installed 10.04, did you use a program called Wubi to install or did you install by restarting the system then selecting to boot from the CD, which would mean that you had to select shich partition to install Ubuntu?

---

### Post by oscarrodas on 2010-03-24
Hi, I did the install from within windows and because didn't have any luck I did boot from the iso disk, which found my windows 7 and offered to install side by side, then I asigned half the disk to Ubuntu and the istallation went ahead. I did check in the tab named advanced and the following info dev/sdb1
Also I tried the following commands fom a different post.
 
set root=(loop0)
linux /boot/wlinux-2.6.31-14-generic root= /dev/sda2 loop=/ubuntu/disks/root.disk ro
 
but get the message: UNKNOWN FILE SYSTEM, even tried using dev/sdb1 with same result.
Tahnk you.

---

### Post by kaldor on 2010-03-24
> **oscarrodas said:**
> Hi, I did the install from within windows and because didn't have any luck I did boot from the iso disk, which found my windows 7 and offered to install side by side, then I asigned half the disk to Ubuntu and the istallation went ahead. I did check in the tab named advanced and the following info dev/sdb1
Also I tried the following commands fom a different post.
 
set root=(loop0)
linux /boot/wlinux-2.6.31-14-generic root= /dev/sda2 loop=/ubuntu/disks/root.disk ro
 
but get the message: UNKNOWN FILE SYSTEM, even tried using dev/sdb1 with same result.
Tahnk you.

Disc wouldn't boot AND wubi installation isn't working. Sounds like a badly burnt disc. Re-download and re-burn Ubuntu. Make sure you use a low write-speed (8x or less for best results; I use 4) or something may go wrong. 

Good luck.

---

### Post by ranch hand on 2010-03-25
Also make sure that you run the md5sum on the ISO file after downloading it.

I think that I would get a newer image while you are at it.  We are running on the 1.6.32-17 kernel.  1.6.31 is a 9.10 kernel.

---

### Post by oscarrodas on 2010-03-25
Thanks for the sugestion but it didn't work, burned new disc and did insert disc and did and installation from cd, after deleting all the old partitions containing Ubuntu, installed the system but at start uo the problem is different: get two options, windows 7 which start ok, and Ubuntu, when I choose this option I get the message that windows failed to start and I need A copy of windows to fix the problem, I guess I'll give it a miss, delete Ubuntu and continue with Windows 7, thank you anyway for the sugestions.
Oscar

---

### Post by oscarrodas on 2010-03-26
Hi there, today I downloaded the beta 1 of Lucid and solved all my problems, but I had to manually specify where Grub was to be installed. Thanks to all for the input.

---

### Post by ranch hand on 2010-03-26
And the question is?

---

