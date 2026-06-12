---
title: "grub rescue command. grub not working in ubuntu 13"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by pranish on 2013-07-18
[h=5][SIZE=2]I have dual boot ubuntu and windows. When i started my machine, it  started with grub rescue > command. I researched but couldn't solve  the problem. So i tried to act as installing fresh windows 7 and deleted  the ubuntu hard drive. But this also didn't solve the problem. now i  have a screen saying grub rescue > without ubuntu installed in my  laptop. So how to recover?? Remember, i had deleted the ubuntu setup  files installed in my laptop
[/SIZE][/h]

---

### Post by oldfred on 2013-07-18
The grub boot loader in the MBR is just a small part of boot code and needs the rest of grub in the Ubuntu partition to boot.
You can restore a Windows boot loader with your Windows repairCD or flash drive.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Also you can install a Windows type boot loader with this to boot Windows.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

