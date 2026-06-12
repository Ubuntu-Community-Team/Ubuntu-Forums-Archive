---
title: "GRUB not working after resizing NTFS &amp; EXT3 partitions."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by ian75 on 2007-12-19
Hi All,

I think I may have really screwed GRUB after resizing the existing Windows and Linux partitions.

I finally decided the time was right to move away from windows (for about 95% of the time anyway). I already had ubuntu installed on my PC and used Partition Magic to resize the existing NTFS & ext3 partitions. This seemed to go OK but when I rebooted I get the following error:

GRUB Loading Stage 1.5 - it just hangs at that point.

So I rebooted with a GRUB floppy and I can get into Ubuntu. I then tried to use GRUB to reinstall it into the MBR:

1. sudo GRUB
2. find /boot/grub/stage1 - this returns (hd0,5)
3. root (hd0,5)
4. setup (hd0), which returns....

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

Here's the output from fdisk....

omitting empty partition (5)

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ed64b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         447     3590496   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         448        6822    51207187+   7  HPFS/NTFS
/dev/sda3            6954       19929   104229720    f  W95 Ext'd (LBA)
/dev/sda4            6823        6953     1052257+  82  Linux swap / Solaris
/dev/sda5            6954       19929   104229685   83  Linux

Partition table entries are not in disk order

Also here is the output from menu.lst for GRUB.....

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c72208b9-bee9-43c3-bee
e-984a93be2da2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c72208b9-bee9-43c3-bee
e-984a93be2da2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Please help, I've come so far in finally moving from Windows. Don't want to have failed at the final hurdle.

---

### Post by timcredible on 2007-12-19
did you decrease the size of xp and increase the size of ext3?  since xp was there first (i'm assuming), then you moved the beginning of the ext3 partition, which i think will require a re-format and re-installation of linux on that partition.  you can mess with the end of a partition without hurting any of the files on it, but i don't think you can mess with the beginning without hurting the file structure.

---

### Post by ThaRabbit on 2007-12-19
Did you remove a partition in the process of resizing?u

---

### Post by psusi on 2007-12-19
I don't know why find is returning (hd0,5) because you don't have one.  Use (hd0,4).

---

### Post by ian75 on 2007-12-19
Didn't remove the partition just decreased the size of XP (which is the first partition) and increased the size of the ext3 partition. So its looking like a reinstall of Ubuntu from the live CD? A reinstall wouldn't be the end of the world but is there nothing else I can do?

Also totally agree about the comment regarding (hd0,5). However when I'm in GRUB and I use tab to discover the partitions, (hd0,4) isn't an option?

---

### Post by PerJensen on 2007-12-19
what does fdisk report about your partitions ?

could you post the result of 'sudo fdisk /dev/hda -l' 

/Per

---

### Post by ian75 on 2007-12-19
ran the command and it gives.......

omitting empty partition (5)

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ed64b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         447     3590496   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         448        6822    51207187+   7  HPFS/NTFS
/dev/sda3            6954       19929   104229720    f  W95 Ext'd (LBA)
/dev/sda4            6823        6953     1052257+  82  Linux swap / Solaris
/dev/sda5            6954       19929   104229685   83  Linux

Partition table entries are not in disk order

---

### Post by PerJensen on 2007-12-19
well, hd(0,5) in Grub speak is /dev/sda6 which you don't have.

The comment from fdisk "omitting empty partition (5)", I dont't know the significance of, is your partition /dev/sda5 in fact empty ?

When you start grub from a boot diskette, what are your commands ?

I normally done this:

- hit 'c' when grub menu is displayed
- set the root disk: 'root hd(0,X) where X is you boot partition, ie the partition where /boot resides. /dev/sd4 correcsponds to hd(0,4)
-set the kernel: 'kernel /something', tab your way down 
-set the initrd: 'initrd /something', tab your way down
- boot the kernel: 'boot'

what are your exact commands to boot the the linux kernel  ?

/Per

---

### Post by PerJensen on 2007-12-19
bommer

hd(0,4) corresponds to /dev/sda5

/Per

---

### Post by ThaRabbit on 2007-12-19
Run this command and post the output:
```
ls -l /dev/disk/by-uuid/
```

Goal: Check if the UUID is still correct.

---

### Post by ian75 on 2007-12-19
ls -l /dev/disk/by-uuid/ gives....

total 0
lrwxrwxrwx 1 root root 10 2007-12-19 22:41 7bd164cf-c839-4f0d-b98c-c3e58c76b703                                                                             -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-12-19 22:41 A8B2-5B3F -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-12-19 22:41 c72208b9-bee9-43c3-beee-984a93be2da2                                                                             -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-12-19 22:41 F4E0A890E0A85B1E -> ../../sda2

---

### Post by ian75 on 2007-12-19
When I boot from floppy I have a copy of menu.lst. The strange thing is that its pointing to (hd0,5) or (sda6) which I don't have. However I can successfully boot into ubuntu using hd0,5?

---

### Post by PerJensen on 2007-12-19
Doesn't make sense

You have 2 disks  ?, or a USB device plugged in or something similar ?

Instead of using the menu.lst, could you drop into grub commandline  and manually use the root, kernel, initrd and boot commands ?

/Per

---

### Post by ThaRabbit on 2007-12-19
does the bootfloppy include a device.map file? (in the grub folder)

cross reference that file's content (just open with nano or vi) with the device.map file on your hard drive (/boot/grub/)

---

### Post by ian75 on 2007-12-20
I'm not booting off a USB and I only have 1 disk (SDA). 

I also don't have the device.map file in the boot floppy.

As far as I can tell linux is there and is working i.e. I can boot into it via the boot floppy. It just so happens that the boot floppy is pointing to (hd0,5). When I try to update grub from the command line to use (hd0,5) I get grub error 22: No such partition so I can't boot as normal.

I would suspect that my Windows partition is fine as well. My only problem is that I can't boot into any of them via grub. I can only get into Ubuntu from the boot floppy.

Would a reinstall of grub help? I'm getting desperate now. I would loath to reinstall Ubuntu seeing as it just appears that grub may be the problem.

---

### Post by PerJensen on 2007-12-20
Ian, 

could you post the content of menu.lst. Please use the actual file on the boot floppy and not another file you think is similar.

/Per

---

### Post by ukripper on 2007-12-20
Try fixing from Super grub disk.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by ian75 on 2007-12-20
Here's the menu.lst from the boot floppy which can successfully boot to Ubuntu only...

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c72208b9-bee9-43c3-beee-984a93be2da2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c72208b9-bee9-43c3-beee-984a93be2da2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by PerJensen on 2007-12-20
I don't get it.

One thing that my caught my eye is, /boot/grub/menu.lst on your disk is using hd(0,4) and the working menu.lst on your floppy is using hd(0,5).

Have you tried to use hd(0,5) in /boot/grub/menu.lst and reinstall grub the way you show in your initial post ?

/Per

---

### Post by ian75 on 2007-12-20
yep, already tried that :)

Always get  Error 22: No such partition :(

Apparently there is another alternative regarding using the live CD and going through an install using the manual partition method. However I'm sure that the 7.10 live CD forces you to format the / mount point which obviously I don't want to do.

This is not looking good. I only hope that if I do have to reinstall that my existing windows partition will still be ok as well.

---

### Post by PerJensen on 2007-12-20
I am afraid I am out of ideas, if you reinstall, be sure to use the manual partition setup, that way you can preserve the XP installation

/Per

---

### Post by ian75 on 2007-12-20
Thanks for all you help Per. I may soldier on a bit more to see if I can figure it out.

---

### Post by psusi on 2007-12-20
I'm sorry, it should be (hd0,3), not 4.  The extended partition does not count.

---

### Post by ian75 on 2007-12-20
FIXED :-D

Thanks to ukripper for his suggeston of using the following site:

Try fixing from Super grub disk.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Here's the steps I went through:

1. Downloaded and burned the ISO to a CD-R.
2. Rebooted and loaded up the Super Grub menu.
3. Super Grub disk with help.
4. Choose a language.
5. I ran through the help file until I got to the next Super Grub menu.
6. GNU/Linux
7. Fix boot of Linux (Grub)
8. Choose the partition with the Grub files on it - it actually only gave me 1 option.
9. Run it and then reboot.

There are actually a whole host of options available that I didn't even look at but it's definitely a tool with a lot of promise.

So after a day of struggling I've finally got Ubuntu back in all its glory. Thanks to everyone for their help. Super Grub is indeed super :)
[B]
Bye Bye Windoze[/B]

---

### Post by ukripper on 2007-12-21
> **ian75 said:**
> FIXED :-D

Thanks to ukripper for his suggeston of using the following site:

Try fixing from Super grub disk.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Here's the steps I went through:

1. Downloaded and burned the ISO to a CD-R.
2. Rebooted and loaded up the Super Grub menu.
3. Super Grub disk with help.
4. Choose a language.
5. I ran through the help file until I got to the next Super Grub menu.
6. GNU/Linux
7. Fix boot of Linux (Grub)
8. Choose the partition with the Grub files on it - it actually only gave me 1 option.
9. Run it and then reboot.

There are actually a whole host of options available that I didn't even look at but it's definitely a tool with a lot of promise.

So after a day of struggling I've finally got Ubuntu back in all its glory. Thanks to everyone for their help. Super Grub is indeed super :)
[B]
Bye Bye Windoze[/B]

Good job done mate.

---

