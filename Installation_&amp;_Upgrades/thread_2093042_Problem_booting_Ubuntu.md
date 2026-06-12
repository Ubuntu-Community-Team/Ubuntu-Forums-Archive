---
title: "Problem booting Ubuntu"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by Gimmesumdeath on 2012-12-09
Hi!

I installed Ubuntu 12.04 then I installed Windows 7 on my computer, now i can boot in to Windows 7 but not Ubuntu.

I tried to use EasyBCD 2.0 and added an entry for the Ubuntu 12.04 but it dosnt work.

Anyone knows how I can boot back in to Ubuntu?

/ Cheers

---

### Post by oldfred on 2012-12-09
Welcome to the forums.

Most of us use grub2 as the boot loader in the MBR. A few that primarily boot Windows 7 have posted EasyBCD does work, but it creates a work around on grub2's boot loader as it has to be installed to the PBR - partition boot sector which is not recommended (but can be done.)

They have their own forum.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

    
But if you want to boot with grub2 in the MBR, you can download Boot-Repair into the Ubuntu install when in LiveCD mode.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


Or you can just use a few commands to reinstall grub2 directly. New versions need liveCD to be same version.
       
 [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

