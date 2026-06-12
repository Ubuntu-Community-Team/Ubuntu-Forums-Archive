---
title: "how to burn DVD with multiple insallatin iso's and other supporting data"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by twinturbotom on 2013-02-18
I have several computers with varying architectures (32 & 64 bit).  Each machine also requires unique driver sets to download (like B43 firmware/drivers for wireless connection).  I also have other files that make setting up a machine easier.  I'd like to make this stuff available on the same DVD or USB but not sure where to start.  Before I go burning DVD's with data and with fire after ruining them.  Anyone have some thoughts on how to approach this?

I've read I can de-construct an iso and add to it, but that won't work with 2 ubuntu live installs; I see how I could de-consruct my 64bit iso and add a new folder and data to it.

I've also read and thought that I could treat it like a drive that can be partitioned?  Not sure I understand the mechanics of properly setting that up.  Multiple, selectable, bootable partitions on a DVD: 3 partitions, 1 for 32bit, 1 for 64 bit, and 1 for supporting documentation... Would the DVD need its own boot loader?

I'm looking into this thread as a solution now: [thread]("http://ubuntuforums.org/showthread.php?t=1763451&referrerid=1776707")[URL="http://ubuntuforums.org/showthread.php?t=1763451"]
[/URL] 
Any thoughts or direction would be greatly appreciated...

---

### Post by offgridguy on 2013-02-18
There is some info in this thread.

[http://ubuntuforums.org/showthread.php?t=2081785](http://ubuntuforums.org/showthread.php?t=2081785)

---

### Post by Bashing-om on 2013-02-18
twinturbotom; Hi !

I ran across these that you may find of interest:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)


[INDENT]regards

[/INDENT]

---

### Post by twinturbotom on 2013-02-18
Thanks for the direction Offgrid and Bashing.  I'll read up and attempt somethings in your references; I appreciate the direction!  Thanks.

---

### Post by twinturbotom on 2013-02-19
The problem with the pre-built tools appears that ubuntu 12.10 isn't a supported distro!
So I'm not burning 32 and 64 isos based on a manual approach:
[here]("http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu")

Still not sure how I can add supporting files without unpacking each installation iso and customizing the liveCD... which is pretty cool.  Although I just wanted to have a directory with files after installs versus customizing each install.  We'll see where it goes.

Thanks.  You're replies have been very insightful

---

### Post by axel668 on 2013-02-19
you might be able to do something similar with USB sticks and Unetbootin, as described here:

[http://tazbuntu.blogspot.de/2009/05/multibootin-with-unetbootin.html](http://tazbuntu.blogspot.de/2009/05/multibootin-with-unetbootin.html)

---

### Post by oldfred on 2013-02-19
I put multiple Ubuntus, gparted, parted magic and other repair ISO all on one flash drive. And then I copy some install scripts that I use and some of my notes on how to do things all on one flash drive.

       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda

    
There now are scripts that automate the multi-ISO install.
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

Flash drive is really seen as another hard drive, so this also has details on ISO booting.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by twinturbotom on 2013-02-26
Thank you all for the wealth of information!  I greatly appreciate it!

---

