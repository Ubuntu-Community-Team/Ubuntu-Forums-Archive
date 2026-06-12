---
title: "Perplexed about InitRD"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by wbarnes on 2006-03-13
I know that initrd is an initial ramdisk and it holds various driver modules (ie ide, scsi, tape, etc) needed by the kernel to mount drives and filesystem.  

If I understand correctly, after the bootloader completes its job, the initrd (ramdisk) is created and the initrd image file placed onto it.  The image file contains all the device/file system modules needed by the kernel to access the device/file system.  Once the kernel loads the modules (from the ramdisk) it then has capability to mount the device file system.  Once the file system is mounted, the initrd is disposed of.

It has been explained to me that the initrd solves the chicken before the egg problem.  ie. the kernel can't mount the file system without first loading req'd driver....but this required driver is on the file system that it can't yet mount.

That made sense to me until I noticed that in grub's menu.lst, both the kernel and the initrd point to the same device, /dev/hda3.   Why is it that the initrd's image file can be accessed from the device but the kernel can't access what it needs? 

2nd question: whose role is it to create the ramdisk and load the image file to it - would it be the boot loader or the kernel?

Thanks

Thanks

Bill

---

### Post by stuporglue on 2006-03-13
> That made sense to me until I noticed that in grub's menu.lst, both the kernel and the initrd point to the same device, /dev/hda3. Why is it that the initrd's image file can be accessed from the device but the kernel can't access what it needs?

Someone can correct me on this if I've understood incorrectly. Bootloaders have to have some sort of access to the file system. I believe that with Grub accesses your Linux partition in ext2 read-only mode to start with. With the disk in RO mode, it accesses the initrd and loads it into memory. Once it's in memory, grub gives up the controll. 

> 2nd question: whose role is it to create the ramdisk and load the image file to it - would it be the boot loader or the kernel?

Again, someone may need to correct me, but I think that Grub loads the image into RAM. The initrd however, is already created and exists on the disk at /boot/initrd.img-(Kernel Number). 

If your initrd just isn't cutting it for you (missing a module needed to boot or something), you can edit the files in /etc/mkinitramfs and run "sudo dpkg-reconfigure linux-image-`uname -r`" and a new initrd.img will be created for your current kernel. 

Hope that helps

---

### Post by wbarnes on 2006-03-13
What is the point of the boot loader loading the initrd image.  If the boot loader can access the drive, why can't the kernel?

---

