---
title: "GRUB dies after one booting of Windows"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by thecomputerdude on 2008-02-04
Hey all, got a strange problem here. 

I just decided that I wanted to have a dual boot of Windows XP and Ubuntu 7.10 64bit. I got Ubuntu running, and for several boot cycles, no problems. However, when I used Grub to boot to Windows something squashed it. I don't know exactly what happened to it, just I'd get the screen that was where Grub was just beginning to load then it would crash and reboot. After several cycles of this I just did a Windows Fixmbr and Fixboot, so I could at least use my computer.

I've seen dozens of threads on Grub here and how to repair it, but I wasn't able to fix it through a live boot. 

Anyways, I'll post up what I guess are important facts. 

I have 4 SATA drives
Windows is on sdd3 partition 0 and Ubuntu is on partition 1 (I think), so they're on the same drive but different partitions
I've had this install of Windows x86 32bit for 3 months
I'm trying to use Ubuntu 7.10 x86 64bit (I have a Pentium 4 660)
I have already gotten just about all my Ubuntu stuff working right, I had just installed Flash and Java. 
Anything else you need to know, just ask. 

So given this information, what would you suggest is the best course to take with this issue? I don't want to reinstall Ubuntu all over, I'd much rather patch it up with a live boot. But at the same time, I don't want to be left depending on Grub as a bootloader. 

Is there a way to boot Ubuntu through the Windows bootloader, possibly by editing the boot.ini file in some way? 

I've got what I guess is above average technical knowledge and I'm not afraid to try complicated stuff if necessary. I'm kinda new to Linux overall, although I've been using a hard drive install of Knoppix for over a year now.

---

### Post by logos34 on 2008-02-05
boot from the ubuntu live cd.  

>Places>computer>click on ubuntu root to mount

go to /boot/grub and post your **menu.lst** file

also, post output of 
[B]
sudo fdisk -l[/B]

Yes, you can boot linux from windows.  You could try [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html") in the meantime, until you can fix grub.

---

### Post by thecomputerdude on 2008-02-05
The Menu.lst file is blank, I checked that just earlier. 

I also figured out the drive is in it's death throes, or something like that, because it suddenly started disappearing mid-boot to Windows. No amount of fixboot or fixmbr will solve that problem. It's a 7 month old 80GB Raptor, kinda early for it to die. I replaced the SATA cable because one of the connector ends looked damaged, hope that it will start working correctly.

Right now I'm reinstalling WinXP to drive 0 in an attempt to go back in to the Raptor and back up my  files. I think I'm going to leave Ubuntu on the Raptor and see what happens.

---

