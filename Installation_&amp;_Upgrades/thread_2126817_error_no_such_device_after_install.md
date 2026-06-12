---
title: "error: no such device after install"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by Deskpro1 on 2013-03-18
I have made a serious blunder while trying to install Ubuntu  12.04. on my HP G5000 laptop.

I had a sata hard disk plugged into a USB  docking station while I was downloading Ubuntu 12.04 

to a disc. Somehow I got 12.04 on the new disk and now, when I start up the laptop, the following error message 

appears

error: no such device : C4d5732d - 3c18 - 4818 - 86e2 -bca076dd9929
grub rescue>

and it won't boot up  to Windows Vista or Ubuntu.

However, if I plug in the sata hard disk docking station, I get the GNU grub version 1.99-21ubuntu3.9 boot option screen

with

Ubuntu, with Linux 3.5.0-25 generic
Ubuntu, with linux 3.5.0-25 generic (recovery mode)
previous Linux versions
Memory test (memtest86+, )
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader0 (on /dev/sda2)

I can choose either vista or ubuntu and they will load OK.

How do I rectify this please?

Thanks in anticipation!!

---

### Post by long2511mdd on 2013-03-18
There are some ways for you to boot into your system again, those mechanisms are in Ubuntu Documents>Grub2

You can reinstall your Grub 2 to use your bootloader or fix it if you want. It is better if you have live CD or live-usb to install. Both terminal and graphical tools are useful. For instance:

"
When using a LiveCD, due to GRUB 2 changes between  Ubuntu releases, it is recommended that the user boots a LiveCD of the  same release (11.10, 12.04, etc) as the release to be repaired. If the  user has installed a different version of GRUB 2, use a LiveCD with the  same GRUB 2 version. If necessary, use the *fdisk* command to help determine the partition on which Ubuntu is installed. The *fdisk* option "-l" is a lowercase "L". Look for one of the appropriate size or formatting. Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The ' 


[LIST]
[*]
sudo fdisk -l sudo blkid
[/LIST]
In the following commands: 


[LIST]
[*]Use the partition number of the Ubuntu installation with *mount* command. 


[*]Do **not** use the partition number with the *grub-install* command. 


[*]**X** is the drive letter (a, b, c, etc.); **Y** is the partition number (1, 5, etc). 


[*]*--boot-directory* is the folder in which the GRUB folder is located. This is normally */boot* but should be changed if the *grub* folder is located elsewhere. 


[*]On systems with a separate */boot* partition, that partition should be mounted to */mnt/boot*. For instance: sudo mount /dev/sda6 /mnt/boot 


[*]grub-install will restore missing files in the *grub*  folder but will not restore intentionally deleted or corrupted files.  To accomplish these tasks GRUB 2 must be completely removed and  reinstalled. 

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda**If Ubuntu is installed on B-tree file system i.e. btrfs** then */boot* changes to */@/boot* in above commands such that : 

sudo grub-install --boot-directory=/mnt/@/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/@/boot /dev/sda**For GRUB 2 version 1.98 and earlier (Ubuntu 10.04)**, the installation command is slightly different. Rather than designating the *--boot-directory*, the switch is *--root-directory*. In this case, the location changes to */mnt* 

sudo grub-install --root-directory=/mnt /dev/sdX

"


[/LIST]

---

