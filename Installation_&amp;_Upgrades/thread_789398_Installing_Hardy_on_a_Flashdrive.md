---
title: "Installing Hardy on a Flashdrive"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by LonelyTraveler on 2008-05-10
I'm trying to install Hardy on my flashdrive in order to use it at work. I've tried using PendriveLinux, but it tells me to copy files from the live cd that is not even on there. Like the ubuntu.ico file. Any other way of getting this done? Thanks.

---

### Post by Pumalite on 2008-05-10
From another thread:

 Re: Installation from USB Stick
i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

    * use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
    * copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
    * rename isolinux.cfg to syslinux.cfg
    * goto [http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/](http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/) and download the initrd.gz and vmlinuz files.
    * create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
    * copy the ubuntu iso you wish to install onto the root of the usb stick


whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps
__________________

---

### Post by LonelyTraveler on 2008-05-10
> **Pumalite said:**
> From another thread:

 Re: Installation from USB Stick
i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

    * use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
    * copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
    * rename isolinux.cfg to syslinux.cfg
    * goto [http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/](http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/) and download the initrd.gz and vmlinuz files.
    * create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
    * copy the ubuntu iso you wish to install onto the root of the usb stick


whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps
__________________

Im not too sure if you are understanding me right. I don't want to install from the flashdrive. I want to install on the flash drive. As if it is a harddrive.

---

### Post by Pumalite on 2008-05-10
Sorry:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by LonelyTraveler on 2008-05-10
Thanks Pumalite. Been trying to get this to work for hours, but can't get it. Seems like the startup files for Hardy differs. The problem too is that I don't have the disctree directory on my life cd for one. Anybody here got this to work? Please me me know.

---

