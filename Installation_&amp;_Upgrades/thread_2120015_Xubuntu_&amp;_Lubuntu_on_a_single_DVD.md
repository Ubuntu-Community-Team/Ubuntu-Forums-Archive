---
title: "Xubuntu &amp; Lubuntu on a single DVD"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by mercurial88 on 2013-02-25
Is there a way to burn Ubuntu, Xubuntu and Lubuntu on a single DVD on Win 7 & Ubuntu ?. I tried burning Xubuntu and Lubuntu on a single DVD using Magic ISO but that didn't go to well. So i was hoping i could get some idea's if it's possible. 

Thanks.:guitar:

---

### Post by oldfred on 2013-02-25
I have multiple installs on one flash drive.

These are for flash drives, but I did it manually before scripts became available.
       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

    
       CD/DVD multiboot
multicd.sh - combine Linux ISOS into one - syslinux boot loader or isolinux.cfg 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

   How to create an Ubuntu All-in-one Live DVD uses grub4dos
[http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html](http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html)

   Older but procedure is same.
[http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu](http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu)

---

### Post by mercurial88 on 2013-02-25
Sweet, thanks for the quick and prompt reply, would have been a pain burning them on single DVD, with so much space left to spare. 

Quick question though how do i go around making a multi bootalbe .iso file? i can't seem to get multi cd to work. 

i created a folder in documents, with all the necessary .iso (Ubuntu and Puppy) extracted multi cd, though i can't seem to get multi cd to work :(.

---

### Post by mercurial88 on 2013-02-25
> **istealth shadow said:**
> No. You need 3 DVDs. Or you can use 3 USB sticks.
although you don't really need that many linux installations....

Oh that's cuz I've been introducing friends and family to the world of ubuntu, but not all of them have good enough pc's to run Ubuntu. Some have like really old system like P3 and all so i can work out which will suit their system best and provide optimum performance. Hence, i am inclined to burn all the distros on 1 DVD.

---

### Post by oldfred on 2013-02-26
I have not done a DVD, just flash drives. 

But it is not one ISO, you copy each ISO and have some tools to boot the ISO. 

A magazine I recently purchased has each ISO extracted on the DVD but had some software to boot each system.

Flash drives work a bit better if the computer will boot a flash drive. But only computers in about the last 6 years or so boot from USB flash drives. The flash drive you can update with new versions easily and load a bit faster.

But if computer does not boot from flash drive it will not run full Ubuntu anyway. Ubuntu is a full featured system. Older systems may need the Xubuntu or Lubuntu or other lightweight systems. Real old systems also may not have PAE extensions. 
But my 6 year old laptop boots from flash, only has 1.5GB of RAM and runs the 64bit version of Ubuntu. But I do change to use gnome-panel not Unity.

---

### Post by mercurial88 on 2013-02-26
I was originally planning on booting from flash drive but had none empty. Thanks for the info will try finding and booting from a flash drive :P

---

