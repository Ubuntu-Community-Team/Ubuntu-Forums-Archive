---
title: "Grub Error 22 when external drive is plugged in"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Smoother on 2007-10-28
Hi.

I have been looking for a solution of this problem for quite some time, but everything related to the problem has to do with installed linux distributions on external drives.

This is not the case for my system.
Ubunte 7.10 is on a partition of my first hard drive together with Windows XP. Booting is fine when no external hard drive is plugged in, but once I plug in an external USB hard drive or a USB memory stick, I get Grub Error 22.

I believe that the problem must have shown up earlier.

If you need the menu.lst or the fdist -l output, please let me know.

---

### Post by meierfra on 2007-10-28
Try this : Change your boot order in the bios so that  the internal drive  comes before the usb   drive.

If this does not work post the output of "cat /boot/grub/menu.lst". Also plug in your usb-drive, boot from a live cd and post the  output of "sudo fdisk -l".

---

### Post by Smoother on 2007-10-28
Ok, but how do I add the USB drive to the menu.lst?

I installed Ubuntu without the USB drive and when I plug it in before I boot, the problem shows up and not when I plug it in after I booted. 
Therefore I don't have a menu.lst entry for the USB drive.
The also have 3 different USB drives that want to plug in once in a while.
Isn't there a generic solution to the problem?

---

### Post by meierfra on 2007-10-28
Did you try changing the boot order?

---

### Post by mlind on 2007-10-28
are you using UUID's in your /etc/fstab and grub's /boot/grub/menu.lst ?

---

### Post by Smoother on 2007-10-29
Hi. 

I use UUID's, but as I said earlier, there are no entries for my USB drives.
Once I have booted Ubuntu and I plug my USB drives in, they are recognized automatically.

This is my menu.lst:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb5bb7c3-5d0f-47d8-ba74-e30884024d80 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb5bb7c3-5d0f-47d8-ba74-e30884024d80 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

And my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fb5bb7c3-5d0f-47d8-ba74-e30884024d80 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=083075BC3075B174 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=300077CB00779696 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=A8588F78588F4452 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=7CC3-1C9E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=6C38A27A38A242C6 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=9CD014B9D0149C18 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=740a7a4e-b83d-40f6-b5f9-6bce6bd78894 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I don't have any entries for the USB drives, because they are not always plugged in.

Is this the problem?
What do I need to do when I have more than one USB drive plugged in at startup?

Thanks again.

---

### Post by meierfra on 2007-10-29
> I don't have any entries for the USB drives, because they are not always plugged in.
Is this the problem?

No. But I'm confused. Your usb-drive seems to appear in your fstab:


> # /dev/hda1
UUID=083075BC3075B174 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=300077CB00779696 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=A8588F78588F4452 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0     

Or are these partitions on an second internal drive.

> 

What do I need to do when I have more than one USB drive plugged in at startup?

Well, I'm still  waiting for your response to the following:

1)   Did your try changing the boot order in the bios?

2) With your usb-drive plugged  before boot up, type "sudo fdisk -l" in a terminal and post the output here.

One more question: Did you  edit your menu.lst and change (hd0,2) to (hd1,2)?

---

### Post by uguwoo on 2007-12-23
I also have that problem. I have an Acer laptop AS9810.
It took me many hours of staying up late at night and fooling with "supergrub" before realizing what the problem was.

Apparently when the USB external hard drive is plugged in "hd0" becomes "hd1" and hd1 becomes hd2. That is what is fooling Grub!
That is what I saw when listing the drives in Supergrub.

I'm not sure what is causing that yet but it may be something to do with the BIOS. In this case there is nothing wrong with the MBR!
Editing the menu.lst won't change anything either because Grub is fooled to the wrong partition even before it gets to the menu.lst. It can't find the correct partition!
I am surprised that this was not found and fixed before.

(Also by the way, while I'm in a writing mood) the server version does detect the Windows OS's and writes a correct menu.lst for Grub.
The desktop version 7.10 does not detect any other OS's!

---

### Post by meierfra on 2007-12-23
> Apparently when the USB external hard drive is plugged in "hd0" becomes "hd1" and hd1 becomes hd2. That is what is fooling Grub!

I am aware of this. That is why I suggested to Smoother to change the boot order in the BIOS. If the external drive comes after the internal drive in the boot order, then the internal drive should be (hd0) and the external (hd1). 

Did you try changing the boot order?

If changing the boot order in the bios does not help, you can still reinstall grub and edit menu.lst to boot ubuntu. But then you would always have to have the external drive plugged  in in order to boot.

---

### Post by alyndaker on 2008-04-26
Did we ever find a solution to this problem?

Like the original poster, I can boot normally with the USB-HD powered down and turn it on after boot, but this isn't a good solution for me.  With the previous install, I had to have the drive powered on at boot, but I'd like to get away from that.

To start, I changed the boot order in the bios (with USB-HD not even selected) to all possible combinations of HDs with no avail. Per the other suggestions, I looked at fdisk -l, device.map, menu.lst, and fstab but everything appears to be in the correct place.  I've used UUIDs where I can and the USBHD seems to be mapped to /dev/sdc.

Here's the output from fdisk -l when booting from the LiveCD:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000578bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4864    19535040   83  Linux

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x852a852a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cfd9349

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           5       40131    c  W95 FAT32 (LBA)
/dev/sdc2               6       60801   488343870   83  Linux

```

I'm open to any suggestions...

---

### Post by Ng Oon-Ee on 2008-06-20
Hi alyndaker, I realize your post is from 2 months back, but I came across it while searching for my own solution to this same problem. I've solved it now, so I thought I'd post what's needed.

When you boot up with the USB drive (in my case its an eSATA drive, but same concept) plugged in, the /dev/sda or /dev/sdb order gets messed up. To correct this, you need some way of uniquely identifying the partition to be used as root. Queerly enough, this is done using the UUID (which I suppose means Universally Unique IDentifier from a quick google).

First step is to find this UUID, second step is to instruct your GRUB loader to load this UUID as the root filesystem.

**[SIZE="5"]FIRST STEP[/SIZE]**

Firstly, to find the UUID for all your current partitions, open the terminal and type

```
sudo blkid
```

The result should look something like this:-

```
/dev/sda1: UUID="B288286788282BF3" TYPE="ntfs" 
/dev/sdb1: UUID="4EF4B223F4B20D69" TYPE="ntfs" 
/dev/sdb2: UUID="C4AC2CC7AC2CB5B8" LABEL="Data Drive" TYPE="ntfs" 
/dev/sdb3: UUID="0f89a3c5-abb6-463c-ae3c-2e38406702d6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="c91de528-fbcc-48c8-abdf-8cb8f73e5126" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="2bc9b814-818f-461c-9c33-0bc9ce584c52" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="39503553-8383-45e1-9c6c-7677dd7e03b6" 
```

In my case, my root partition is /dev/sdb6 (which would be /dev/sda6 if my external harddisc, currently /dev/sda1, was not on during bootup). If you're not sure which partition is your root partition, type in the terminal:-

```
sudo gedit /etc/fstab
```

It will either look like this (only a snippet posted):-

```
# /dev/sda6
UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c91de528-fbcc-48c8-abdf-8cb8f73e5126 /boot           ext3    relatime        0       2
```

or something like this (ditto):-

```
# /dev/sda6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5 /boot           ext3    relatime        0       2
```

In any case, the correct partition would be the one with a single backslash (the root filesystem). Be VERY CAREFUL not to save the fstab file, messing up this file can cause your system not to mount important folders.

**[SIZE="5"]SECOND STEP[/SIZE]**

Once you have the correct UUID, you have to edit the GRUB menu. First, back it up with this first line, then edit it with this second line:-

```
sudo cp /boot/grub/menu.lst /boot/grub/menulst.backup
sudo gedit /boot/grub/menu.lst
```

This is a very long file, if you have to time read the very informative piece on it at [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm"), which is where I got the information which finally solved this problem.

Anyway, basically you have to search for the portion (its towards the bottom) which looks like this:-

```
## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,4)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Note that the 'root' points to /dev/sda6, which is fine when my external is not loaded,  but should be /dev/sdb6 when it is. Instead of using this 'changing' identifire, we replace it with the UUID, as below:-

```
## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,4)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Now, whether your external is plugged in on boot-up or not shouldn't matter, your Ubuntu will be A-okay in any case.


Note, messing with GRUB's menu.lst is a hazardous procedure. What I did while testing this (I got it wrong a few times) was to replace the root=/dev/sda6 with the UUID for the (recovery mode) option, leaving the normal boot option intact. Then, when you see the GRUB menu, select the recovery mode option to test, if it doesn't work, just boot from the first option. If it loads till the recovery menu (4 options, didn't really take a look at them) then you'll know you've successfully did everything.

Phew, that was long. Hope it helps someone.

---

