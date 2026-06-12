---
title: "new installation as multi-boot, replacing existing linux"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by stephendlynch on 2010-04-29
Hello!

Exciting!  I'm about to try to install Ubuntu (9.10, 64-bit) on my desktop.  The machine already has a version of Linux on it (SUSE LED 10.2), and is a multi-OS machine (boots EITHER in Linux OR in Windows XP-64).

I have not been able to find much that explicitly talks about installing Ubuntu in a multi-OS configuration, so I thought I'd put out a quick query for some pointers.  

For example, will the installation program give me the option of leaving the Windows disks (2 of the 4 internal drives) intact, reformat the 2 drives containing all the existing Linux stuff, AND offer the option of rewriting the master boot record to change the options from SUSE/WinXP to Ubuntu/WinXP? 

Anything else I should be aware of or watch out for?  

THANK YOU ! ! ! 

-stephen

---

### Post by limey_rick on 2010-04-29
When you install Ubuntu, when the partition manger runs, it will allow you to select the disk on which to install. If you want to overwrite your existing SUSE setup, you can do that. 

You may want to boot the Live CD and then start Ubuntu though without installing so you can remove any partitions you don't want (SUSE ones for example) so that when you come to install, you have already defined partitions the right size and where you want them. 

Ubuntu will install GRUB (bootloader) so make sure its installed on the MBR of the first BIOS selected disk. To check this, after the partition manager has selected where you will install, and before you actually commit to installing on the disks, there is an advanced option you can select, where you tell GRUB on which disk to install itself on. Boot this disk and GRUB should recognize your windows installations and other OSs.

Don't worry if the installation completes 100% ok and when you boot you start windows and don't see GRUB. It just means that GRUB has installed in the MBR of another disk, so try to change the disk order in the BIOS, or re-install GRUB on the correct disk.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

