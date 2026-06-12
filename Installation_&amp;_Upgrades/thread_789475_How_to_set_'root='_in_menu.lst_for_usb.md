---
title: "How to set 'root=' in menu.lst for usb"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by redblue123 on 2008-05-10
I have Hardy installed in persistent mode on a USB flash drive. It boots using syslinux and syslinux.cfg.  All works fine.

I'd like to change boot manager to grub4dos (in part to boot an iso file).  I need to figure out what to enter for root= in menu.lst.  Nothing I can think of works - I get a kernel panic regarding bad root device.

I first tried to figure out the UUID of the usb.
/etc/fstab does not list anything useful
I tried using ls -l /dev/disk/by-uuid, but using the values from that did not help.  
I tried /dev/sda, /dev/sda1, /dev/sdb, /dev/sdb1, but no joy there

My relevant syslinux.cfg includes:

LABEL live
  menu label ^Run Ubuntu in Persistent Mode
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash --


The failing menu.lst includes:
title Hardy
root (hd0,0)
kernel /casper/vmlinuz root=/dev/sda1
initird /casper/initrd.gz
boot

Any suggestions would be appreciated.

---

### Post by Pumalite on 2008-05-10
Run 'blkid' in the Terminal with your USB plugged in.

---

### Post by redblue123 on 2008-05-10
blkid got me:
/dev/sdb1: SEC_TYPE="msdos" LABEL="UBUNTU8" UUID="08CC-4937" TYPE="vfat" 
/dev/sdb3: LABEL="casper-rw" UUID="2b72950b-e01e-4016-8d18-6fc73d106db6" TYPE="ext2" 

root="08CC-4937" and root="2b72950b-e01e-4016-8d18-6fc73d106db6"

failed with the same old error message:

VFS: cannot open root device "08CC-4937" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

Too bad it doesn't list any available partitions.

As mentioned, it boots fine through syslinux, so I'm confident things are otherwise ok.  By the way, I'm launching grub through syslinux by an entry in syslinux.cfg.

---

### Post by Rallg on 2008-05-10
I have Ubuntu 8.04 amd64, i386, and Windows bootable from my USB using Grub4Dos. There is a trick:

When I installed Ubuntu, I had the installer place Grub on the same hard drive partition as Ubuntu (for each version). I'm not sure that's necessary, but I wanted to look at what was written for the menu.lst in each case. Since my MBR was unaltered (it boots directly to Windows without the USB inserted and selected), the Grub installations are not actually used.

I created a bootable USB with DOS, and Grub4DOS. Then I copied one of the menu.lst files from my hard drive, and (IMPORTANT! THIS IS THE TRICK!) changed references from (hd0,n) to (hd1,n) for partitions (various n). The reason is that on the USB, Grub4DOS thinks that the USB is hd0, and that the hard drive is hd1.

Other than that I did not need to make any changes in menu.lst except for my own options. Just keep in mind that when you update a kernel, or change a partition (by moving, re-sizing, etc.) you will have to manually edit the menu.lst on the USB, since "automagic" won't find it there.

---

### Post by redblue123 on 2008-05-10
I don't have ubuntu on my hard drive, so I don't have a grub installed menu.lst.  Also, grub4dos is doing a fine job of launching ubuntu, the problem is the root= kernel parameter being passed to ubuntu.

What root= setting do you have?

By the way, root=UUID=[number] doesn't work any better than root=[number]

---

### Post by Pumalite on 2008-05-10
You can replace UUID. For root=/dev/xxx (where xxx is your USB

---

### Post by redblue123 on 2008-05-10
What xxx do you suggest?  USB is typically /dev/sdb, but that didn't work (see first post in this thread)

---

### Post by redblue123 on 2008-05-11
Tried 3 versions:

title Hardy dev
root (hd0,0)
kernel /casper/vmlinuz boot=casper root=/dev/sdb1 
initird /casper/initrd.gz
==> This failed

title hardy ramdisk
root (hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw splash persistent
initrd /casper/initrd.gz
boot 
==>  This seems to work

title Hardy from syslinux.cfg
root (hd0,0)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash persistent 
initrd /casper/initrd.gz
==> Typing from this now

---

### Post by Pumalite on 2008-05-11
You might want to read this:
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)

---

### Post by redblue123 on 2008-05-11
> **Pumalite said:**
> You might want to read this:
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
See post #17 in that thread

---

