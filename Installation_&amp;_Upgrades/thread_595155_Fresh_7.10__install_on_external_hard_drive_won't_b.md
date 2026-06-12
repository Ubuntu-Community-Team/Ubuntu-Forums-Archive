---
title: "Fresh 7.10  install on external hard drive won't boot"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by JKB2 on 2007-10-28
I am trying to install 7.10 onto an external usb hard drive.  The livecd works fine, the md5 sum checked.  The install from the livecd seems to work.  My bios can boot from usb, I've gotten FreeBSD to boot and run off this setup.  When I go to boot off the drive however, I get the screen with an F1 and some other stuff (F1 is the only option as I want to use my bios to choose which OS to boot, and want to keep them completely separate).   I did not install GRUB.

When I get this screen, any key presses give me a system beep.  It also beeps every 15 seconds or so if I just let it sit.

I'm running an IBM Thinkpad R51 and trying to boot off a 20gb laptop hd in an enclosure.

Do I need to install GRUB?  If I do, I want it on the external, so that if it is not plugged in it will automatically boot off the internal.

Is there something I'm missing?  It's not spitting any errors back; it's not doing anything.

Thanks for your help,
John Best

---

### Post by logos34 on 2007-10-28
You need a bootloader.

Reinstall ubuntu but this time put grub on the MBR of the USB.  Change default location to (hd1) or /dev/sda (or sdb depending on how gutsy installer sees your drives).

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(post#502)

---

### Post by megahertz on 2007-10-28
First, boot with the Gutsy live CD (Ubuntu 7.10)
Second, find how Gutsy is seeing your Hd's.
Using terminal:
sudo fdisk -l

It will be something like below
Disk /dev/hda: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x057b3228



   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1        9729    78148161    b  W95 FAT32
 *(hda1 means HD master, partition 1)


Disk /dev/hdb: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00075cf8



   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1   *           1        4678    37576003+  83  Linux
   *(hdb1 means HD slave, partition 1)
/dev/hdb2            4679        4865     1502077+   5  Extended

/dev/hdb5            4679        4865     1502046   82  Linux swap / Solaris


Third find where Grub (boot loader) was installed
sudo grub (to enter the grub program)
To find Grub was installed
grub> find /boot/grub/stage1

 (hd1,0)
 * (hd1,0 is = hdb1 and means HD, partition 1)
grub>quit (to quit he grub program)

If Grub isn't installed, you can install it with the live CD (remember to match your external HD ID with the command that install grub – see below )
hda1=hd0,0 (probably your internal HD)
hdb1=hd1,0 (probably your external HD)

Grub installation
Quick Start



This option will use the Desktop/Live CD to install Grub into your MBR (Master Boot Record). This option will overwrite your Windows Boot Loader It is OK to do this, in fact that is the goal of this how to (in order to boot Ubuntu) 



1. Boot the Desktop/Live CD.



2. Open a terminal (Applications -> Accessories -> Terminal)



3. Start grub as root with the following command :



 sudo grub



4. You will get a grub prompt. 


   GNU GRUB  version 0.97  (640K lower / 3072K upper memory) 



 [ Minimal BASH-like line editing is supported.  For the first word, TAB

   lists possible command completions.  Anywhere else TAB lists the possible

   completions of a device/filename.]





grub> root (hd1,0) #Hit the <Enter> key
  (says that root is on hdb partition 1)


grub> setup (hd1) #Hit <Enter> key  (install 
grub on MBR on hdb


grub> quit #Hit <Enter> key, quits grub



5. Reboot (to hard drive). Grub should be installed on your external HD


6. If, after installing grub, Ubuntu does not boot you may need to edit /boot/grub/menu.lst (That is a small "L" and not the number 1 in menu.lst)



    *



      Open a terminal and enter :


Using terminal:
 gksu gedit /boot/grub/menu.lst
 ( opens the file /boot/grub/menu.lst
 in gedit)
* at the very end you find the grub boot menu

title		Ubuntu 7.10, kernel 2.6.22-14-generic

root		(hd1,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9593f956-5cd8-4c9c-bb6d-6b049ae6ab98 ro quiet splash

initrd		/boot/initrd.img-2.6.22-14-generic

quiet



title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root		(hd1,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9593f956-5cd8-4c9c-bb6d-6b049ae6ab98 ro single

initrd		/boot/initrd.img-2.6.22-14-generic



title		Ubuntu 7.10, memtest86+

root		(hd1,0)

kernel		/boot/memtest86+.bin

quiet


     If it looks like above and still doesn't boot try to replace (hd1,0) by (hd0,0) (don't ask me why, but it worked with me), save the file and reboot.

---

