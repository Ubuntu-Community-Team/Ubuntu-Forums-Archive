---
title: "Install 10.04 but get blank boot menu (only the option to boot from CD)"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by fregeslogic on 2012-10-31
Hi all , I am new to Ubuntu. 

I'm tring to run 10.04 on a friend's laptop. I've installed it with 30gs of EXT 2 partition and 2gs of SWAP on 32gs SSD. Installation went smoothly until restart.

I keep getting a blank boot menu with only the option of booting from CD (and hte order is set so that Hard Drive boot is higher ranked than CD boot).

Why won't the laptop recognise Ubuntu's installation? 

Many thanks for the help.

---

### Post by oldfred on 2012-10-31
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

How old/new is computer?

Is BIOS in AHCI mode? And some other BIOS settings can make a difference like Quickboot/fastboot which should be off. 

Is SSD only drive in computer? Grub defaults its install to sda.

---

