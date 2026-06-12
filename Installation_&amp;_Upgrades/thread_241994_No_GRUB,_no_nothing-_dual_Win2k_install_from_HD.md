---
title: "No GRUB, no nothing- dual Win2k install from HD"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by lancer on 2006-08-23
Hi all,

I'm trying to set-up a dual-boot setup with Win2k and Dapper Drake using GRUB from my HD since I don't have a bootable CD.  I'm attempting this on an IBM Thinkpad 560X laptop.
 
I've found many instructions on the topic, which I've followed, yet when I restart my machine it automatically starts loading Win2k and I never even get a GRUB boot options screen.  I just can't see what I'm doing wrong here.  Any ideas?
 
I've got Win2k installed on a NTFS partition (hd0,0), my linux kernel from Ubuntu Dapper Drake and the initrd in C:\boot. I've copied two files from GRUB, grldr is in C:\, and menu.lst is in C:\boot\grub\. 
 
I've also tried having menu.lst in C:\ after reading that 
"Update: starting from version 0.4.0pre4, grldr will now only look for F:\menu.lst and not for F:\boot\grub\menu.lst anymore."
 
My boot.ini looks like this:
 
 [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
C:\="Microsoft Windows"
C:\GRLDR="Start Grub"
-------------------------------------------------
and my menu.lst:
 
timeout 10
 
title Windows at (hd0,0)
root (hd0,0)
chainloader +1
 
title Ubuntu Installer at (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz
--------------------------------------------------
 
I've tried with manually copying the two GRUB files from GRUBforDOS 0.4.1 and also using the GUI with WinGrub 0.02.06.
 
Nothing happens.  Win2k just loads as usual.  Isn't something supposed to happen? What am I missing?](*,)

---

