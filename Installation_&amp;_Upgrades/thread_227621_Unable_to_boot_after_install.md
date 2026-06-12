---
title: "Unable to boot after install"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by j5moore on 2006-08-02
Downloaded and installed ubuntu-6.06-server-i386.iso, using server option.  Get the following when attempting to boot:

GRUB Loading stage1.5.


GRUB loading, please wait...

---

### Post by encompass on 2006-08-02
could you please be more descriptive.
Hard drive setup and dual boot and errors during install system setup and speed. etc etc.-

---

### Post by j5moore on 2006-08-02
Loaded on AMD-K6-2/500, 20Gb drive, boot to Ubuntu only.

Used the following options to load:

Install a server
Entire 20Gb drive (no LVM option)

Only errors during installation of security modules.

In the process of reloading again.

---

### Post by j5moore on 2006-08-02
No errors in second installation, but same results, freezes during GRUB loading message.

---

### Post by j5moore on 2006-08-02
Sorry, forgot to add memory to hw configuration:

AMD-K6-2/500, 20Gb HDD, 128 MB RAM

Also correction on disk downloaded and used:
ubuntu-6.06-alternate-i386.iso

Again loading Ubuntu as stand-alone server, no dual boot.

Let me know if you need more HW/SW specific information.

---

### Post by j5moore on 2006-08-03
AMD-K6-2/500, 20Gb HDD, 128 MB RAM

Now, downloaded this image: ubuntu-6.06-server-i386.iso

Install a LAMP server
Entire 20Gb drive (no LVM option)

Get the following at boot, then freezes:

GRUB Loading stage1.5.


GRUB loading, please wait...

Then same install with Entire 20Gb drive using LVM:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15

---

### Post by encompass on 2006-08-03
I found this...
> Grub error 15
After hitting return in the grub prompt you get something similar to this one?
Code:
Booting 'gentoo Linux'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel (hd0,0)/boot/kernel-2.4.20 root=/dev/hda3 vga=792

Error 15: File not found
Press any key to continue...
info grub wrote:
15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

If it's the kernel that it's missing (bzImage, kernel...):make sure that the file it is referring to exists on your boot partition.

To find out what the exact name of your kernel is, first boot from the live-cd or into your existing linux installation. Then mount /boot if you've got a seperate partition, or mount / if you don't. Then do the following:
Code:
cd /boot
ls
This will list all the kernels that you've got on your boot partition. 
here...
[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)
looks like something did not copy.  or it could be your running under an old grub installation that is looking for something else.
Did you say it had a previous installation of linux on it?

---

### Post by j5moore on 2006-08-03
No previous GRUB installation, this is the first ever install of ubuntu.  Previously I had an old version of Mandrake loaded.

I would assume that the installation that I am selecting would format the drive and totally remove any former information under each partition.  If I need to, I'll boot from a windows floppy and use fdisk to repartition and format the entire drive.  Also, this would also blow any chance of booting from the former installation, since I have deleted all information from at least the former Mandrake install.

Booting to live-cd, would this mean booting up the install cd and installing manually and looking at the partition information during the install?  Or is there another menu option that I should use?

I am getting no prompts after the Error 15, it is just hung.  Does not respond to any keyboard action (return, alt-cntl-del, etc.)

I downloaded the server image twice, because I had a bad cd burn the first go around and thought the distro might be bad, and downloaded from a second source, but the cksum was the same on both images.  So I get the same conditions on two different image loads (server, alternate).

I'm really hoping to get this up and running.  The one thing I like about the LAMP option is because I am getting everything installed that I need, with the exception of perl.  I had issues getting php loaded in Mandrake, so never could get that to work.

---

### Post by j5moore on 2006-08-03
ok, I have booted to cd-rom, selected the rescue option, and got to a prompt to Execute a shell in /dev/Ubuntu/root
I have done that and mounted /boot
in /root I see:
ls -l
vmlinuz -> boot/vmlinuz-2.6.15-23-server
cd /boot
ls
System.map-2.6.15-23-server
abi-2.6.15-23-server
config-2.6.15-23-server
grub
initrd.img-2.6.15-23-server
lost+found
memtest86+.bin
vmlinuz-2.6.15-23-server

so it appears that the kernel exists and is properly linked.

I don't know exactly what is supposed to be under /boot/grub, but here goes:
default
device.map
e2fs_stage1_5
fat_stage1_5
jfs_stage1_5
menu.lst
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5

---

