---
title: "Reversing Grub changes"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by sbt5 on 2010-08-01
[COLOR=black][FONT=Verdana]I have a laptop that is running a OEM version of windows 7. I wanted to install Ubuntu on a usb hard drive, such that when the usb hard was plugged in I could run Linux and when it wasn’t I could boot from the internal hard drive directly into windows 7. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I thought this could be accomplished by just changing the boot sequence in my bios. :([/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Now the computer will not boot unless the usb hard drive is connected and I can reach the boot menu. Is there any way that I can**[FONT=Verdana] reverse the changes that Grub made[/FONT]**? I don’t think there is a repair console in my OEM disk to fix the MBR. I am not experienced with Grub and would hate to have to reload windows back to the initial factory built (they load it up with a lot of junk). Any help would greatly be appreciated.[/FONT][/COLOR]

---

### Post by hansdown on 2010-08-01
Welcome to the forum, sbt5.

The easiest way, for me, at least, is to download gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Boot from the live CD, and click

fix mbr windows.

---

### Post by efflandt on 2010-08-01
You accidentally installed grub to the default location on the mbr of your main hard drive.  If you have not changed anything yet, you could boot to Ubuntu and scroll down to **Changing or Moving GRUB 2** at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Then you could restore the mbr of your main drive to the Windows mbr.

If you already fixed the mbr and now cannot boot Ubuntu from the USB drive, the page above has other methods to fix grub2, or you could reinstall to the USB drive.  But note that when doing a regular install to USB, use the **Advanced** button in the last step (summary screen) before installation proceeds, to put grub in the mbr of the USB drive, instead of default to main hard drive.

---

### Post by sbt5 on 2010-08-01
Thanks to hansdown and efflandt for their replys.;)
 
Having spent a few hours trying to recover using Gpartion, ubuntu live cd and window repair, I am still in the same position.
[LIST]
[*]can not boot without the drive install
[*] get the grub error - no such device found when trying to boot from my internal hard drive
[*]have tried to repair with Gpartion, does not seem to give me the options that I need
[*]windows automated repairs finds no errors; options are to restore point which fails or use the recovery cd
[/LIST]So the only option appears to be with grub itself. I cant seem to load grub from the live cd
 
Thanks

---

### Post by oldfred on 2010-08-01
If you can still boot into Ubuntu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If not you will have to use a liveCD to reinstall grub to the external and windows boot loader to the internal.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by sbt5 on 2010-08-01
Thanks oldfred!!
 
 
 That was exactly what i needed. I download the rescue disk to fix the problem. :D
 
Now I will see if I can boot in ubuntu with the external.

---

