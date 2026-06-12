---
title: "Build Ubuntu installable USB stick"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ftornell on 2011-04-28
Hi,
I was wondering if anyone know if its possible to create a USB stick from where one can install either Ubuntu x86, x64 and Server x64.

Copy each CD image into three subfolders on the stick and then have a menu choosing what type of installation it should be?

---

### Post by nikio on 2011-04-28
Same question for me, and a couple more:
-is it possible to include some programs like skype or clamav in the usb installation?
-if I run ubuntu from the usb stick, and run the update manager, the installation will be already updated?

thank you.

---

### Post by C.S.Cameron on 2011-04-28
Check out MultiBootUSB, you can stick multiple Linux isos on a flash drive and boot them using grub2.
Works really nifty.

---

### Post by C.S.Cameron on 2011-04-28
> **nikio said:**
> Same question for me, and a couple more:
-is it possible to include some programs like skype or clamav in the usb installation?
-if I run ubuntu from the usb stick, and run the update manager, the installation will be already updated?

thank you.

Check out Remastersys.

---

### Post by oldfred on 2011-04-28
How large is the USB? You can do a full install and have ISOs to multi boot also, if 8GB or more.

I did the multiboot of various ISO before the scripts to automate the process can out. Actually just doing one or two is not difficult, finding the exact syntax for the grub loop mount stanza is the biggest issue which the scripts automate.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

If you do a full install then you have to manually add grub entries to loop mount additional ISOs you may want on USB.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

---

