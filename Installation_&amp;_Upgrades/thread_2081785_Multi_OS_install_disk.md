---
title: "Multi OS install disk"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-11-07
I have an install disk by Sardu containing 4 OS.  
When I boot up, regardless of whish OS I choose I get the error message

Unable to find a medium containing a live file system.

Is  this referring to the install disk? Or to my HD.  When I run the hardware detection tool on the disk , it detects everything in my computer.
   Anyone else experienced something like this?
                                                                        Thank you.

---

### Post by offgridguy on 2012-11-07
An update here;  The seller i bought this from offered this explanation

[COLOR=#000][FONT=arial]"Since  the disc does not appear damaged it is possible there is some sort of  hardware incompatibility. It may be with the boot loader for the ISOs  and not with the Ubuntu versions themselves".

I have made arrangements with the seller, for 2 replacement disk's, one with kubuntu and
one with xubuntu.  This solves my issue, someone may have thoughts about his
explanation.
[/FONT][/COLOR]

---

### Post by oldfred on 2012-11-08
You can make your own multi-boot DVDs or flash drives. I have several Ubuntus & repairISO all on one flash drive. I did it manually before scripts were available.

These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

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

### Post by grahammechanical on 2012-11-08
If the BIOS is set to boot from the CD/DVD drive and it loads some sort of menu, then the issue is with the CD/DVD. Surely, when you remove the disk and reboot it must boot into the OS on the hard disk? Unless the hard disk does not have an OS on it either.

May be this disk has 4 ISO images that have been copied on to it and not burned to it in a way that will let you load either of them.

Regards.

---

### Post by offgridguy on 2012-11-08
> **grahammechanical said:**
> If the BIOS is set to boot from the CD/DVD drive and it loads some sort of menu, then the issue is with the CD/DVD. Surely, when you remove the disk and reboot it must boot into the OS on the hard disk? Unless the hard disk does not have an OS on it either.

May be this disk has 4 ISO images that have been copied on to it and not burned to it in a way that will let you load either of them.

Regards.
Correct on  all counts,  I agree with the last point, although the seller would disagree.
      Thank you for the input.

---

### Post by offgridguy on 2012-11-08
Thank you, oldfred;  I will work my way through this.

---

