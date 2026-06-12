---
title: "Ubuntu installation Failure on i7 Asus Fx-Pro laptop Geforce 960M"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by jesung1221 on 2016-12-30
[ 4.742136] nouveau 0000:01:00.0: priv:HUBO:10ecc0 ffffffff(1e40822c)
    [ 5.549068] scs1 host3:runtime PM trying to activate child device host3 but parent(1-5:1.0) is not active.


This error message pops up when I did the disk check before installation.
The screen remains at this phase [http://i303.photobucket.com/albums/n...x/IMAG0079.jpg](http://i303.photobucket.com/albums/n...x/IMAG0079.jpg) (loading stage)
and does not proceed.




I have an Asus FX-PRO with NVidia Geforce GTX960M graphics card and an Intel i7-Core CPU.  
I am installing the latest version of Ubuntu.

---

### Post by slickymaster on 2016-12-30
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2016-12-30
Exactly what model? Everything I saw with x-pro was AMD based.
Installing in BIOS or UEFI boot mode?
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 


Do you know if booting with Intel or nVidia chip in control of video. Some systems allow you to set that in UEFI/BIOS, others are automatic.

Are you using nomodeset to boot install media & for first boot or until you install nVidia driver?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Some Asus need another boot parameter to prevent run away log files.

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

