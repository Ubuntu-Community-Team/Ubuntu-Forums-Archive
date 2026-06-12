---
title: "[SOLVED] XP won't load on dual boot"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by chris1991 on 2008-01-04
Hi there. I have a dual boot system set up after following this guide (**[link]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")**) but whenever I try to load windows, I get the following message

```
ERROR 13: Invalid or unsupported executable format

Press any key to continue...

```

Does anyone have any ideas as to how to fix the problem?

Cheers,

Chris

---

### Post by Craigus on 2008-01-04
Discussion here:

[http://ubuntuforums.org/showthread.php?t=282545]("http://ubuntuforums.org/showthread.php?t=282545")

---

### Post by Blindraven on 2008-01-04
Change the entry for windows by issuing the following in a terminal :
Code:

```
sudo gedit /boot/grub/menu.lst
```

Erase the entry you have for windows and replace it with the following : 
Code:
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

---

### Post by logos34 on 2008-01-04
You need to post your /boot/grub/menu.lst and output of

sudo fdisk -l

It's not clear to me if you are dual booting on one or two drives

---

### Post by chris1991 on 2008-01-05
Hi, The current configuration of the menu.lst file is as follows:

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=58c093a9-710d-4b8e-bebd-82383ef6103b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=58c093a9-710d-4b8e-bebd-82383ef6103b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title              Windows XP
root               (hd0,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

The fdisk shows the following:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6808    54685228+  83  Linux
/dev/sda2   *        6809        6932      996030   82  Linux swap / Solaris
/dev/sda3            6933        9728    22458870    7  HPFS/NTFS

```

And I have also attached a screenshot of GParted.

Cheers,

Chris

---

### Post by glennzo on 2008-01-05
You're trying to boot Windows off of your swap partition. Try (hd0,2) as /dev/sda3 is the NTFS partition.

---

### Post by chris1991 on 2008-01-05
Thanks Glennzo, it works perfectly now!!

Thanks again,

Chris

---

### Post by glennzo on 2008-01-05
You're quite welcome Chris.

---

