---
title: "Install Ubuntu 13 from ISO on disk"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by dbiaptis on 2014-01-15
Hello,  I am running into some issues with installing Ubuntu from the disk.
I have downloaded the iso and dumped it onto a separate partition with:
>    dd if=ubuntu-13.10-desktop-amd64.iso of=/dev/sda9 bs=16K 

Afterwards, I have rebooted into grub2 and switched to command mode.
I have executed the following commands:
>  
   set root=(hd0,8)
   linux /boot/vmlinuz.efi boot=casper ubiquity-only root=/dev/sda9
   initrd /casper/initrd.lz   
   boot

However, loading fails with error "Unable to find a medium containing a file system".
This leaves me into some limited shell (busybox). The prompt is "(initramfs)".

I have tried some other boot options as well, none of which worked:
>    linux /boot/vmlinuz.efi boot=casper ubiquity-only root=/dev/sda9 live-media=/dev/sda9
   linux /boot/vmlinuz.efi boot=casper ubiquity-only root=/dev/ram1 ramdisk_size=1048576 rw


If I don't specify root=/dev/sda9, I also get some errors related to no media in /dev/sr0.  I've used something similar
for Ubuntu 12 without any issues. Can you please help me figure out what options should I provide to the kernel to
convince him to treat /dev/sda9 as if it were the cdrom?

---

### Post by oldfred on 2014-01-15
Using the dd command works to install to a flash drive as it is configured as both a DVD or flash drive bootable.
 dd creates hybrid which does not have standard partition table, you need to delete with dd beginning of flash drive to restore it to full size. You have an ISO image not a partition and it may be sr0 or seen as CD drive.

But it cannot be copied to a partition.

You can directly boot an ISO from one partition to install into another unmounted partition (as long as not both in extended or in effect mounted).

      
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

### Post by dbiaptis on 2014-01-15
Thanks, I don't know why I didn't manage to find this by googling.

Here are the commands that I've used:

> 
set root=(hd0,7)
insmod ext2
loopback loop /stefan/downloads/software/ubuntu-13.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz.efi boot=casper ubiquity-only noprompt noeject iso-scan/filename=/stefan/downloads/software/ubuntu-13.10-desktop-amd64.iso toram
initrd (loop)/casper/initrd.lz
boot


---

