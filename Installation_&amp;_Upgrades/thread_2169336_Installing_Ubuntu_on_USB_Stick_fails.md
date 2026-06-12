---
title: "Installing Ubuntu on USB Stick fails"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by einkeks2 on 2013-08-21
Hi there,
I'm trying to install Ubuntu (12.04 Desktop) on a usb drive (Patriot 32GB Tab), but having some trouble so far.

I created a separate Ubuntu Live Stick. 
Started the Live Stick and tried to install on my Patriot usb drive.
I pre-partitioned the usb drive (4GB Swap, 28GB Root).
Installing seemed to work fine, but if I try to boot from the stick I just get a flashing "_" on a black screen and nothing else.

Has anyone an idea what went wrong? 
Did I miss a step? 

Best Regards 
Keks

---

### Post by ubfan1 on 2013-08-21
Assuming you actually installed grub bootloader to the usb target, maybe it's bug 384633, wrong device used.  Take a look (run live media, mount the target somewhere under /mnt (mkdir xx if necessary), and take a look at the grub.cfg file.  On non-UEFI machines, that will be in /mnt/xx/boot/grub/grub.cfg.  Assuming you have a hard disk at hd0/sda, the usb stick should be at hd1/sdb. (Assuming no other disks present).  Where UUIDs are used, they should be ok.  edit the wrong devices (Used to be hd2/sdc, but since the 12.04 series, that may no longer be true), and at the first successful boot, run sudo update grub.

---

### Post by oldfred on 2013-08-21
It could be an install issue, but usually those give an error on not boot loader or grub rescue.

It also could be a video issue. What video card chip do you have.

If only one install grub does not show menu by default. You have to hold shift key from BIOS until menu appears. Some UEFI systems use escape key.

From grub menu you can add nomodeset if a video issue. Use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

