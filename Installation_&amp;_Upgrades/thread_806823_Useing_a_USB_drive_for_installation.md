---
title: "Useing a USB drive for installation"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by jared314 on 2008-05-25
I have a laptop that does not have a CD drive but supports USB boot devices.  Is there any way i could load the ISO for ubuntu onto a USB drive so that i could install it on my laptop?

---

### Post by Pumalite on 2008-05-25
From another thread:

'the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

    * use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
    * copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
    * rename isolinux.cfg to syslinux.cfg
    * goto [http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/](http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/) and download the initrd.gz and vmlinuz files.
    * create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
    * copy the ubuntu iso you wish to install onto the root of the usb stick


whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps'

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

