---
title: "How I Solved the(MY) Dual Boot problem listed on a lot of Posts"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by acaby on 2007-08-14
It was A very Simple solution for me. I have Win98SE/Ubuntu 7.04 on Disk 1. I got an Old 20G ide, put it in as slave and formated and split partitioned 50/50 @ fat32. I am using the first half for file storage for disk 1 and the 2nd Half I installed Ubuntu Ultimate (Do not think it is supported here) which wrote the MBR. I did not have to edit any files in any OS.

The ONLY thing I did to make it dual boot flawlessly was make a few changes to the better old BIOS.

On Boot up (during the showing of the splash screen only) I F1'd (Other Win OS's might be different) the BIOS setup and changed the Boot order of the 2 Hard Drives. Made the Slave Boot 1st. F10 saved and :) Ubuntu Ultimate Popped up.

If I want to use Windows or 7.04 I just Restart, on the windows splash screen repeat the procedure, switch the boot order back to the master drive, F10 and up pops the GRUB, Select the program I want and it loads.

I have been doing this for 2 day's and it has never missed. Other's may not agree with this method but it WORKS for me and I hope maybe it will work for someone else that is having dual boot problems.

ps: I Tried Super Grub Disk for over a week and never could figure out the switch disk method as it was too confusing for me. :confused:(my problem):confused:If anyone is literate in this program then maybe that is the way you should go.

---

