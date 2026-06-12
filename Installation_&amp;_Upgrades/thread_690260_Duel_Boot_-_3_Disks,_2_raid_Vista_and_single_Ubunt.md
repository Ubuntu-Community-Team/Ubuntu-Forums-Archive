---
title: "Duel Boot - 3 Disks, 2 raid Vista and single Ubunto"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Avigrace on 2008-02-07
I have 3 HDD

Disk 1
Disk 2

Both these drives are in raid 0 and there are 2 partitions on it, a main one with vista and a spare one.

Disk 3

I put Ubunto onto this disk


I can boot into either OS if I select which HDD to boot to in the bios, however I would like to either use the grub menu or vista boot loader to choose which I boot to. In Ubunto I installed gparted to see if it could see my raid and it cannot (sees 2 seperate drives) so I assume that I cannot get grub to install to this drive.

In vista I used EasyBCD and created an ubuntu menu and it asked which drive and I set it to the first partition on the Ubunto disk (ext3). when I select this at the boot menu it tries for a second then returns me to the boot menu.

I would prefer to use the Vista boot menu if possible as I have more experience with windows, if anyone has any advice I would greatly appreciate it.

---

### Post by rolandus on 2008-02-11
I am trying to do the exact same thing...

EasyBCD worked for me, but only after I installed GRUB to the first partition of my Ubuntu disk (as opposed to the default location, which is the MBR of the disk itself).  

Here's how I did it in two steps:

Step 1: Install GRUB in the boot partition

 In Ubuntu, start GRUB... (a '>' command prompt should appear)
 $ sudo grub

 Figure out what grub thinks your hard drive is called...
 > find /boot/grub/stage1

 It should say something like "found /boot/grub/stage1 at **(hd2, 0)**"

 Tell grub to set the Ubuntu partition as the root. **Replace (hd2,0) with whatever was returned  from the 'find' command**.
 > root (hd2,0)

 Install grub to the MBR of that partition. **Replace (hd2,0) with whatever was returned  from the 'find' command**.
 > setup (hd2,0)

 Exit from GRUB
 > exit

Step 2: Fix the boot entry using EasyBCD 

 Reboot into Vista. In EasyBCD, when you create a new Linux boot entry, there is a little check box at the bottom that says something like "Grub isn't installed in the MBR". Create a new entry for Ubuntu and make sure that box IS checked. 

Now you should be able to reboot into the Vista bootloader and choose Windows or Linux.

This worked for me with one small problem... Even though GRUB identified my boot partition as (hd2,0), when I went to boot into Ubuntu, the GRUB4DOS (the GRUB image that EasyBCD uses) thought the boot partition was (hd0,0). So... if it still won't boot, go into linux and edit the following file: /boot/grub/menu.lst

$sudo gedit /boot/grub/menu.lst

Find the entry that boots Ubuntu. It should be the un-commented one near the bottom of the file. In that entry, wherever you see (hd2,0) (for example), replace it with (hd0,0). 

This worked for me, but your drives might be plugged in differently, and so have different numbers.

WARNING!!! Although this fixed the boot entry in Vista, I do still have a problem... Every time I boot into Linux, my BIOS "forgets" about my RAID volume. (I am using hardware RAID). This results in my having to go in to the BIOS and "fix" my RAID volume every time I go from Linux to Vista. If you are using software RAID, I strongly suspect that this **won't** happen, but if you are using hardware RAID, it *might* be an issue.

---

