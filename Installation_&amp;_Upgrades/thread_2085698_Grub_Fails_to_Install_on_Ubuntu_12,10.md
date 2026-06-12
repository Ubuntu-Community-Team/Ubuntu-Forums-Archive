---
title: "Grub Fails to Install on Ubuntu 12,10"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by floweringmind on 2012-11-18
I have a GA-Z77X-UD5H Motherboard by Gigabyte. I have windows 7 installed that works fine. Installing Ubuntu 12.10 works fine but grub fails to install, so I only see the windows boot menu. I have tried using EasyBCD 2.2 to book into the drive, but it always fails, so I am at loss.

I am wondering if anyone else has this motherboard and has this problem, maybe I missing a setting.

Chris

---

### Post by oldfred on 2012-11-19
Did you install the 64 bit version of Ubuntu? And is Windows in UEFI mode or BIOS mode. Your motherboard BIOS supports both.

Window & Ubuntu both have be be either UEFI/gpt mode or BIOS/MBR mode to both work. And how you boot install disk is how it will install. 

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

