---
title: "Ubuntu 904 install on Toshiba"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by manishmk on 2010-01-10
I have a Toshiba laptop M35-S359 (Phoenix BIOS 1.30) which already had Win XP home edition.
I tried installing Ubuntu 9.0.4 on a USB 500GB Western digital HDD. The installation went fine but there are two problems:
 
1. The Windows MBR was overwritten by Ubuntu and I get a GRUB error 21 when I boot. I have tried grub-install, grub, etc. 
2. When I remove the internal HDD, it gives an error for it and only then it recognizes the external HDD and boots OK from it.
 
Questions:
1. How do I make it boot from external HDD?  I set the BIOS to boot from external device but doesn't work. Should BIOS be upgraded?
2. How to restore Windows? I do not have the recovery CD.
3. After 1&2, I want to make it dual -bootable. How do you do it afterwards?
 
Thanks in advance.
Manish

---

### Post by tachuela on 2010-01-10
Use Super Grub.
To install follow these guidelines:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by oldfred on 2010-01-10
Supergrub should let you install windows boot to the internal drive and install grub legacy to the external drive. You need to keep track of drive order sda, sdb etc whether external is plugged in or not. Sometimes the external becomes sda when plugged in and the internal is sda when the external is not. If you have grub in the external and the external set to boot first, ubuntu will boot. If windows is then in the internal it will boot.

Windows XP uses the same boot loader as older windows but is different than the boot loader for Vista and 7. 

You can also install the windows older boot loader from a linux live cd.
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr    # where sdX is the drive sda, sdb etc

---

### Post by manishmk on 2010-01-13
Will the BIOS play a part? If I remove the internal HDD, I get an error but then it finds the external HDD and boots Ubuntu! 
Or would the LILO help?
Thanks
Manish

---

### Post by oldfred on 2010-01-13
BIOS determines which drive boots. If you set it to boot the external first it will boot that if found then if not found boot the internal.

You should not normally be removing the internal drive as various settings in both windows (drive 0 or drive 1) and Ubuntu/grub (sda or sdb). Then when you plug the drive back in the setting may change, so the system is looking in the wrong place.  The external may think it is the wrong drive and not boot correctly.

---

### Post by manishmk on 2010-01-14
I do set it to external device, but it does not boot from it unless first drive is removed. I did that just to check if external is recognized at all or not. There is no USB option in the BIOS. that's the problem.

---

### Post by tachuela on 2010-01-14
Big problem.

---

### Post by oldfred on 2010-01-14
If you can boot from the external with the internal not installed are you booting from a USB connection? Or have you plugged it in, in place of the internal?

On my desktop the boot from USB is not under USB but is under harddrives. I could not get a USB stick to boot for the longest time as I tried every USB setting. It had USB floppy, USB Cd, etc but none would boot the USB key. For some reason I left it in and happened to look at boot (hard) drives in BIOS and it was one of the choices.:)

---

### Post by oldfred on 2010-01-14
[http://ubuntuforums.org/showthread.php?t=1380027](http://ubuntuforums.org/showthread.php?t=1380027)

You have two threads I did not know others were working on you problem in that thread.

---

