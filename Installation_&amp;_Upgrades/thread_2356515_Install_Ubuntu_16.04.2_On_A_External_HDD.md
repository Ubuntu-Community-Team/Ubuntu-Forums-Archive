---
title: "Install Ubuntu 16.04.2 On A External HDD"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2017-03-23
On my laptop I have Xbuntu 16.04.  I want to install Ubuntu LTS 16.04.2 to my Seagate barracuda.  Little did I know I couldn't just burn it onto a flash drive and have both the flash drive and external HDD hooked up via USB and boot to the flash drive and write it to the external.   I've read that I can do a write it to my external from my computer and then just boot to the external from my laptop.  I however didn't see the procedure.  Could someone help me out?  :confused:

---

### Post by ubfan1 on 2017-03-24
Why do you think you can't burn the ISO to a flash, and use it to install to an USB external HDD?   There are issues on UEFI machines doing this: 1)The grub bootloaders get installed to the internal HDD's ESP instead of the external HDD's.  2) After copying the internal ESP to the external ESP, grub and shim still need to be copied to /EFI/Boot and shimx64.efi renamed to bootx64.efi  3) A secure boot shimx64.efi nvram entry for the internal HDD may be changed to grubx64.efi, which wont work with secure boot enabled (so you need to change it back with efibootmgr).  All pretty straightforward.
  Legacy has no such problems, just target the external disk for the bootloader location.  Now if you boot from the external disk, it should offer all installed systems, and if you run the internal installation, and run sudo update-grub, that should pick up the external installation, and offer it when you boot from the internal disk.

---

### Post by oldfred on 2017-03-24
Best to partition in advance, whether UEFI or BIOS based system.
And then use Something Else install option to choose (change) which partition is / (root) and /home if desired. 

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader (only works with BIOS boot installs).
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by C.S.Cameron on 2017-03-25
If you make an ext partition on the external drive and label it casper-rw, the flash drive will use it for persistence when booted with the persistent option.

---

### Post by shane_faulkinbury2 on 2017-03-26
The problem is guys that my motherboard only has one HDD connector therefore I have to connect via USB.  So it's either purchase a new motherboard or connect via USB.  I don't have the money to purchase a motherboard so I'm trying the USB route.

Thanks for the links Fred.  They're bookmarked and I'm going to look through them and get this running by the end of the week.  I say that because with work and all!

---

