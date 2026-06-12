---
title: "GRUB not installing"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2010-07-25
My Machine Specs:
 
Dell Inspiron 8600 (Laptop) (Bought sometime in 2003)
Pentium M - 1.4 GHz
512 MB RAM (DDR- the older chip) 
160 GB - IDE Hard Disk
 (SAMSUNG) - (( I usually stick to Seagate but I got this from my bro) 
 
Problem I recently changed my HDD from 40 GB to 160 GB.. I am able to install Windows XP seamlesly. I want to dual boot XP and a Linux OS..I formatted using Gparted and the current allocation of my HDD
 
sda1 - WINDOWS (NTFS) - 40 GB
 
I ran the Ubuntu installation from a USB (created from my HDD ISO img thro Universal USB Installer Ver 1.7.3) ..The install option reg HD is
 
-- Install Linux using maximum continous free space ( I have not partitioned the remaining 120 GB)
 
The Installer ran Gparted and formatted EXt 4 and the system was installed
 
However , on reboot , the system drops to a Grub prompt and gives the error " Out of Disk"
 
I tried with many Linux inst CD (Mandriva, Open SUSE , Mint ) ...**Either I get the above error or Grub Error No 17..**
 
I tried installing Linux alone (Kubuntu - 10.04) and it is installed flawlessly on a blank HDD
 
But when I try to install Windows First and try to install Linux ,invariably the boot loader fails (Grub or Grub2)
 
Is there a special method to install for IDE drives?...I have 3 other new laptops and SATA poses no problem...I think this may not be the reason
 
But no distro seems to install alongside windows
 
Can anyone pl guide me on this?
 
I am afraid since Grub is the problem , I am not able to give any scr shot
 
I tried using utilities like Super Grub Disk . I am planning to try System Rescue ..But this will only recover and the same problem will occur when I try to re-install
 
Thanks for your help in Advance

---

### Post by wilee-nilee on 2010-07-25
I think your HD may be beyond the stock bios size, the out of disk may be a clue. I quickly looked on google, and HD size max for this model and all were smaller, but there may be a bios firmware that changes this.

---

### Post by vikrang on 2010-07-27
Actually there is some problem GRUB is having with my machine,,,Except Kubuntu Lucid , others dont seem to install  even on a stand alone basis... Too bad I had wanted to have this is a Linux only machine with 2-3 distros .

---

### Post by vikrang on 2010-07-30
You are right ..When I ran a Live CD of Freespire , it was detecting the NTFS partition but an exclamation symbol in a triangle was embossed in the Icon .When I read the information - It is saying it is a bad block and not able to read the contents of the drive..Reg Firmware - BIOS I have version A14 which was the latest update for my config.Any idea if it would work If I downgrade? or can I try a driver for a different model or make?? Anyway thanks for your help,,,,For the time being it is Windoze!

---

