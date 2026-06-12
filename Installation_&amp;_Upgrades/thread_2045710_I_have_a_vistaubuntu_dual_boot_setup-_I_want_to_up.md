---
title: "I have a vista/ubuntu dual boot setup- I want to upgrade vista will the affect ...."
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2012-08-21
I have a Vista/Ubuntu dual boot set up (with Grub to manage it). I am about to upgrade from vista home basic 32 bit to windows 7 ultimate. Before I do though- I want to make sure that this will not mess with my boot loader. 

I remember that when I was setting up my PC- I had to specifically install windows first and then ubuntu because the windows boot loader does not play very nicely with other operating systems. I just wanted to know if anybody here has experience with this and how would I go about doing this without messing up my boot up settings.

---

### Post by oldfred on 2012-08-21
Windows will install its boot loader to the MBR. You need a liveCD of the current version of Ubuntu or other repairCDs to reinstall grub2 to the MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

And if you want a gui:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

