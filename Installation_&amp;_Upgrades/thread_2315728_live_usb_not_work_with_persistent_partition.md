---
title: "live usb not work with persistent partition"
date: 2016-03-02
forum: Installation &amp; Upgrades
---

### Post by billypon on 2016-03-02
I followed these steps creating my live usb:
1. parted two partitions: one is fat32, one is ext4 without journal(labeled casper-rw)
2. tried creating boot usb by UUI/unetbootin, and then deleted persistent file
3. tried booting with persistent file/partition
4. with persistent file: work fine.
5. with persistent partition: stay in terminal, and I can see 'initramfs' prompt

---

### Post by sudodus on 2016-03-02
Welcome to the Ubuntu Forums :-)

1. Is it enough to get a persistent live drive drive of an Ubuntu flavour, ToriOS or Debian Jessie, or

2. are you trying with another linux distro, or do you want help to fix the system you have, so that it works?

-o-

***If 1:*** Try another tool, which creates persistence with a partition automatically, ***mkusb***. It works with the Ubuntu flavours, with ToriOS and with Debian Jessie. See the following links

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

-o-

***If 2:*** It looks like you have done things correctly. But there is some detail, that is wrong.

***What linux distro and version*** are you trying to make persistent live?

Post the ***output of the following commands*** in a terminal window, when booted live-only from the USB drive

```
df
```
```
sudo parted -ls
```
```
sudo lsblk -ls
```

Put the output within [noparse]```
tags
```[/noparse] to make it easier to read :-)

---

### Post by C.S.Cameron on 2016-03-02
I think persistent casper-rw partitions are not working with Ubuntu 64bit 14.04 and later, created using SDC or UNetbootin.
It should work with recent 32bit Ubuntu or 12.04 64 bit.
If you need persistent 64bit 14.04 + you can do a grub2/iso install, (MultiBootUSB), or do a Full install, (if you have the disk space).

Oops, I forgot to mention mkusb comes with built-in persistent partition.

---

### Post by sudodus on 2016-03-02
32-bit and 64-bit versions of Ubuntu and Debian can be made persistent live with mkusb, and it works in BIOS mode as well as in UEFI mode. MultiBootUSB works too (as recommended by C.S.Cameron) and might work with other distros too (other than based on Ubuntu and Debian).

---

### Post by billypon on 2016-03-04
[https://drive.google.com/file/d/0B0vynHsskQAgYlhxdElJM09KaFE/view](https://drive.google.com/file/d/0B0vynHsskQAgYlhxdElJM09KaFE/view)

my os is mint 17.3, but ubuntu mate 15 is also

---

### Post by billypon on 2016-03-04
ok, I will try mkusb

---

### Post by sudodus on 2016-03-04
Good luck :-)

Please come back and share your result. If you have problems, please describe the details, and I will try to help.

---

### Post by billypon on 2016-03-04
wow, it's cool~
mkusb works fine!!
thanks you all!!!

---

### Post by sudodus on 2016-03-04
I'm glad it works :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

It helps other people to find your solution. After marking it solved the thread will remain open, and you can ask more questions related to the persistent live system. But if you have a new and unrelated problem, you will probably get better help in a new thread with a good title describing the new problem.

---

### Post by billypon on 2016-03-04
but, I want to create another partition for home-rw
how shoud I do?
can I use gparted?
mkusb will wipe the whole disk each time(`mkusb wipe-1` is also).

---

### Post by billypon on 2016-03-04
mkusb has wipe menu: create GUID partition table.
but it's useless, because install operation will re-create all partitions.

can I do these with mkusb:
1. I don't need the "usbdata" partition
2. create another partition for home-rw
3. re-use disk without wipe the whole disk, so that I can save home-rw(casper-rw can be wiped)

so I want to usb, and I can create partitions manually

---

### Post by sudodus on 2016-03-04
> **billypon said:**
> but, I want to create another partition for home-rw
how shoud I do?
can I use gparted?
mkusb will wipe the whole disk each time(`mkusb wipe-1` is also).

Yes, you can use ***gparted*** (directly, not via mkusb).

> **billypon said:**
> Can I do these with mkusb:
1. I don't need the "usbdata" partition
2. create another partition for home-rw
3. re-use disk without wipe the whole disk, so that I can save home-rw(casper-rw can be wiped)

so I want to usb, and I can create partitions manually

You can re-format 'usbdata' to ext4 and give it the label 'home-rw'. It is a good idea to have both of them: 'casper-rw' for persistent changes of the root partition and 'home-rw'  for persistent changes of the home partition.

---

### Post by billypon on 2016-03-04
but install operation will re-create all partitions

---

### Post by sudodus on 2016-03-04
You need not install again. Use ***gparted directly (not via mkusb)*** and edit the 'usbdata' partition - change it to a 'home-rw' partition with an ext4 (or ext2) file system.

---

### Post by billypon on 2016-03-04
and how do I do, when I want to update os?
use dd directly, and format the casper-rw partition?

---

### Post by billypon on 2016-03-04
> **billypon said:**
> can I use gparted?

I mean use gparted to create partitions, and use mkusb to install.

---

### Post by sudodus on 2016-03-04
Well, if you want to keep the os up to date there are several options.

1. Use an installed system (installed like installed into an internal drive, but in this case installed into a USB pendrive or USB SSD drive).


2. Persistent live system:

- Backup the /home directory of casper-rw partition or the home-rw partition if you make one

- Install a new system with mkusb

- Restore from the backup (to get your personal files and tweaks)


3. If you intend to update very often (for example like I do for iso-testing Lubuntu Xenial Xerus now), you can use another system, which boots from iso files.

You simply update the iso files and backup the casper-rw (and home-rw) partition(s). Sometimes you need to restore from the backup to match the new iso file. See the following links

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

and particularly

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

...

Post #49. [A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

---

### Post by sudodus on 2016-03-04
> **billypon said:**
> I mean use gparted to create partitions, and use mkusb to install.

In the particular case with mkusb you do it in the opposite order: 1 - mkusb; 2 - gparted

---

### Post by billypon on 2016-03-04
thanks @sudodus!
I use mkusb install system, and then use parted do these:
1. resize casper-rw
2. resize userdata
3. change userdata to 'home-rw' partition with an ext4 file system

but when I used mkusb, I selected ISO, not usb-pack_efi.
and I found and ISO partition, no ISO file.
if I want to you another system, can I use `dd if=xxx.iso of=/dev/sda4 bs=4096` directly(if space enough)?

---

### Post by sudodus on 2016-03-04
It means that the ***boot system*** is grabbed directly from the iso file (not from usb-pack_efi). In both cases mkusb flashes the iso file into /dev/sda4.

If you want to use a bigger iso file, you can use gparted and shrink the partition behind it (the casper-rw partition /dev/sda5) and after that expand /dev/sda4 into the now unallocated space. Then there will be space enough for a bigger iso file to be flashed into that partition. But you must also consider possible changes in the boot system, the grub.cfg file. So it can get complicated (depending on what iso file you intend to use).
 
-o-

Maybe it is better for you to select ***method 3.*** from post #17 in this thread and use the grub-n-iso method (and boot directly from iso files as they are).

The reason why I think so is that you seem not satisfied with just using the result made by mkusb. I think you want to understand the details, and you want to tweak your system. That method and those tools are described in post #6 and the following posts of the tutorial thread

[***One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot***](http://ubuntuforums.org/showthread.php?t=2259682)

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

...

Post #49. [A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

There are detailed descriptions in some of the posts, for example post #8, which might help you create exactly what you want :-)

**Post #8.** [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

---

### Post by billypon on 2016-03-04
OK, thanks!
It's helpful.

---

### Post by C.S.Cameron on 2016-03-04
I have not had much luck with persistent partitions when upgrading from one version of Ubuntu to the next.
Some things don't work well.

---

### Post by billypon on 2016-03-04
> **C.S.Cameron said:**
> I have not had much luck with persistent partitions when upgrading from one version of Ubuntu to the next.
Some things don't work well.
there are two partitions: one is casper-rw, another is home-rw.
when upgrading, casper-rw will be wiped, and home-rw will be saved.
so I don't worry about it.  ^_^

---

### Post by sudodus on 2016-03-05
Saving only /home (whether a directory or partition) has worked for me when upgrading the iso file. I think it will work for you.

Good luck :-)

---

### Post by C.S.Cameron on 2016-03-05
Yes, I recall home-rw worked with several versions on a multibood disk
I tried casper-rw and remember the USB booted with a second version but not much worked.
I think it then went corrupt.
Have you considered a Full install?

---

