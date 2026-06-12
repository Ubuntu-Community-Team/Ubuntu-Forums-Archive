---
title: "GRUB Location"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Mike Green9 on 2012-12-11
Hi.

I am about to install Ubuntu 12.1 from a DVD to my Windows 7 desktop.

Currently, I am using EasyBCD to boot either of 2 versions of Windows 7. Using EasyBCD, I would like to add Ubuntu to the list.

I will be installing Ubuntu on to a 20GB partition (ext3) on my second hard disk. I want to ensure that Ubuntu won't install GRUB into the system bootloader - rather install it to the bootsector of the Ubuntu partition. Then I can tell EasyBCD about it. (I do not want Ubunu to touch the system MBR.)

I will install Ubuntu to:**  /dev/sdb4**

My Question
Ubuntu install asks me "Device for Boot Loader Installation". Do I select: **/dev/sdb4**   ??

Thanks for you help,

M...

---

### Post by oldfred on 2012-12-11
That should work. I prefer grub2, but some seem to like EasyBCD.

Understand that grub will complain about installing to a PBR - partition boot sector. It has to use blocklists or hard coded addresses to find the rest of grub. PBR is too small for all the boot code it needs to be able to search for the boot files in the install partition. If on a major upgrade or aggressive fsck the grub files get moved, it will break grub. Then you need liveCD or USB to reinstall grub to the PBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

    
To reinstall to a PBR or /dev/sdb4, you have to add the -f or --force option.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Mike Green9 on 2012-12-19
Thanks. Up and running and loving Ubuntu 12.1



M....

---

