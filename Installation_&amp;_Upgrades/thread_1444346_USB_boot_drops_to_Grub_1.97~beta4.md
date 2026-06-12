---
title: "USB boot drops to Grub 1.97~beta4"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by akapotte on 2010-04-01
**The Problem**
When I boot Ubuntu from the USB I get the following outcome:- 
At best I get droped to "initramfs" prompt.

At worst I do not get anywhere, instead, I am thrown to a "sh:grub>" prompt with text below;

**GNU GRUB version 1.97~beta4**
[Minimal BASH-like line editing is supported. For ... completions ]
sh:grub>

**What I did**
I install liveCD on USB by copying the content and booting from GRUB.

I have "installed" Ubuntu 9.10 (Karma Koala) kernel 2.6.31-14-generic.

The USB is divided in two partitions (see the attached images):
(1) A FAT32 partitions where the root and boot folder are. Also the kernel, initrd and ldlinux.sys files as well as grub and syslinux folder are in this partition i.e. FAT32.
(2) A Linux partition where the rest of LiveCd files are i.e. dists, install, isolinux and etc are in this partition.

I am doing all this in a Dell Laptop **Dell d420**


**Below is what I actually did**
[COLOR="red"]Repartition your USB drive[/COLOR]
sudo cfdisk /dev/sdc
1.	Delete any existing partitions.
2.	Create a new, primary partition.  Make it the entire size of your USB drive minus 730 MB or so.
3.	Create a new, primary partition, covering the 730 MB you left out.
4.	Make the first partition bootable.
5.	Change the type of the first partition to C (Windows FAT32).
6.	Write the new partition table.
7.	Quit the program.

[COLOR="red"]Format the newly created partition for Windows to use[/COLOR]
sudo mkfs.vfat -F 32 -c /dev/sdc1
sudo dosfslabel /dev/sdc1 UBUNTULIVE

[COLOR="red"]Mount the Windows partition[/COLOR]
sudo mkdir -p /media/USBDRIVE
sudo mount /dev/sdc1  /media/USBDRIVE

[COLOR="red"]Install GRUB on the Windows partition of your USB drive[/COLOR]
sudo grub-install --no-floppy --root-directory=/media/USBDRIVE /dev/sdc

[COLOR="red"]Get ISO from CD[/COLOR]
sudo dd if=/dev/cdrom of=/path/to/iso/image.iso
sudo mkdir -p /mnt/isoimage
sudo mount -o loop /path/to/iso/image.iso /mnt/isoimage

[COLOR="red"]Copy the kernel and initial RAM disk from the ISO image to your GRUB directory[/COLOR]
sudo cp /mnt/isoimage/casper/{vmlinuz,initrd.gz} /media/USBDRIVE/boot/
sudo umount /mnt/isoimage
sudo rmdir /mnt/isoimage

[COLOR="red"]Create a persistent file system to store data and customizations[/COLOR]
dd if=/dev/zero of=/media/USBDRIVE/casper-rw bs=1M count=256
mkfs.ext3 -F /media/USBDRIVE/casper-rw

[COLOR="red"]Write the ISO image to the hidden partition[/COLOR]
sudo dd if=/path/to/iso/image.iso of=/dev/sdc2

[COLOR="red"]Create a nice GRUB boot menu[/COLOR]
sudo nano /media/USBDRIVE/boot/grub/grub.conf
default         0
timeout         10
title           Ubuntu (Live)
root            (hd0,0)
kernel          /boot/vmlinuz
initrd          /boot/initrd.gz

[COLOR="red"]Unmount the Windows partition of your USB drive[/COLOR]
sudo umount /media/USBDRIVE
sudo rmdir /media/USBDRIVE

[COLOR="red"]Sync up, then unplug[/COLOR]
sync

**What I have tried**
I have edited the /boot/grub/menu.lst

Also at the grub prompt I did try to use sever options; see below 

sh:grub>insmod /boot/grub/linux.mod
sh:grub>set root=(hd0,1)
sh:grub>linux /boot/vmlinuz root=/dev/sda1 
sh:grub>initrd /boot/initrd
sh:grub>boot

I also tried root=UUID=xxxx

But nothing worked.

Moreover, when I tried the 
sh:grub>loopback loop0 /ubuntu/disks/root.disk

The system complained by saying "/ubuntu/disks/" does not exist.


**Errors**
Please, see attached images 
(I took them by camera phone, hence the quality)

Among other the errors I get are:
mount: mounting /dev/sda1 on /root failed: no such device
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

Depending on the kernel options I used on grub prompt, e.g.:
sh:grub>linux /boot/vmlinuz root=/dev/sda1 

I have had variety of this error
mount: mounting /dev/sda1 on **/root failed**: no such device


**Help/Advice**
I need help/advice.
But, I want to do everything **manually**

I know that there are such possibilities as "*Startup Disk Creator*" and others; but as I said I'd like to do everything **manually**.
It's all about learning, and so far I have learned alot.

But now I need some advice on how to resolve this problem.

---

