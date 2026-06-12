---
title: "Triple boot, need help editing grub to point to the other linux"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by SnowPunk98 on 2007-05-11
I am doing a triple boot on my laptop with Ubuntu, Windows, and another Linux distro. I have all 3 installed and grub works and will boot Ubuntu and Windows. I am trying to edit the menu.lst to add the other linux in as a boot option but I'm not sure where to find the kernel and initrd.

The other linux is installed on (hd0,1) or hda1 whichever you like to refer to it as. I basically just need to know how to write the kernel and initrd line so they are pointing to the 2nd linux kernel and will allow me to boot it.

---

### Post by SnowPunk98 on 2007-05-11
OK so using Gparted it has the following information on the partition I installed the other Linux on. It has no lock icon next to it which all the other partitions do.

Partition: /dev/sda1
Filesystem: reiserfs
Mountpoint: (nothing)

I edited grub to look like the following

title linux
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda1
initrd /boot/splash.initrd

When I select the entry from GRUB I get the following message

Error 17 : Cannot mount selected partition

---

### Post by SnowPunk98 on 2007-05-11
The other linux used LILO here is that config that allowed it to boot successfully

boot = /dev/hda
prompt
timeout = 20
bitmap=/boot/splash.bmp
change-rules
reset
vga = 0x317
image = /boot/vmlinuz
root = /dev/hda1
initrd = /boot/splash.initrd
label linux2
read-only

---

### Post by confused57 on 2007-05-11
You might want to read over this link:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

Go down to the section:
grub>find vmlinuz
then read from there.

I was able to boot Zenwalk(which uses lilo), once I was able to determine the vmlinuz symlink, which was:

title   Zenwalk
root (hd0,2)
kernel /boot/vmlinuz-2.6.20 ro
initrd /boot/initrd.gz
savedefault
boot

I've since deleted the Zenwalk partition, but I don't think I used the initrd entry...reading through the link above should enable you to find the symlink & add an entry to boot your other distro.

---

### Post by SnowPunk98 on 2007-05-14
I'm still not able to find it or get it working.

---

### Post by psusi on 2007-05-14
What is your disk configuration?  Please post the output of fdisk -l

---

### Post by SnowPunk98 on 2007-05-15
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2042        2434     3156772+  83  Linux
/dev/sda2   *           6        2041    16354170    7  HPFS/NTFS
/dev/sda3            2435        4757    18659497+  83  Linux
/dev/sda4            4758        4864      859477+   5  Extended
/dev/sda5            4758        4864      859446   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by psusi on 2007-05-16
What filesystem is sda1 formatted with, and what is the other distro on it?

---

