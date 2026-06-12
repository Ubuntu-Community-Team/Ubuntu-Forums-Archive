---
title: "[Q] Burn 32 and 64bit ubuntu 12.10 on same disk?"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by thelildrummabot on 2013-04-04
Is it possible to install 32 bit and 64 bit ubuntu 12.10 on the same disk? I am on ubuntu if you could tell me how to do it in ubuntu. thanks!

---

### Post by thelildrummabot on 2013-04-04
I want the user to be able to pick which version to install.

---

### Post by Slim Odds on 2013-04-04
Look at using a USB stick installing OS's with YUMI.

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by thelildrummabot on 2013-04-04
I am not looking to install on a flashdrive only disks. I am selling ubuntu to people and am trying to give them both to choose from. (just in case they cant use 64 or they need 64 for some reason)

---

### Post by oldfred on 2013-04-05
I have posted the pendrive link above. There are also these scripts.
 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

But I just do it manually. I install grub to flash drive and copy ISO onto flash drive in a /iso folder.
Now older info:

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

Install to a flash drive is really the same as an install to a second hard drive.
      
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by thelildrummabot on 2013-04-05
So does this allow for multi .iso onone DVD -r
https://help.ubuntu.com/community/Grub2/ISOBoot

---

### Post by oldfred on 2013-04-05
I have not tried it on CD or DVDs.

 CD/DVD multiboot
multicd.sh - combine Linux ISOS into one - syslinux boot loader or isolinux.cfg 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

   How to create an Ubuntu All-in-one Live DVD uses grub4dos
[http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html](http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html)

   Older but procedure is same.
[http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu](http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu)

---

### Post by thelildrummabot on 2013-04-05
Thanks!

---

