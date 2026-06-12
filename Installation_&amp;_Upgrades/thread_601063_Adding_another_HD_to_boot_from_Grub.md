---
title: "Adding another HD to boot from Grub"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by eteixeira on 2007-11-02
Add

Hi.

Sorry my bad English...!

I have installed Ubuntu 7.10 in a new hard-drive on primary IDE/master Gurb installed and working.
I have installer my old WinXPX installation/HD on de primary/slave, and i have access via Ubunto do the NTFS Partition/HD (great).

Since i installed Ubunto without the WinXP drive connected Xp is not an available option in Grub menu.

Can i use Grub to select the OS/HD to boot from?

My actual config:
Primary IDE connector
HD Master (cable select) - Ubuntu 7.10
HD Slave (cable select) - Windows XP


My actual "menu.lst" in /boot/grub is the following:

```
<BOF>
...
skiping default options
...

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75978060-3161-4682-aee5-d353ebf2a3bf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75978060-3161-4682-aee5-d353ebf2a3bf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
<EOF>
```

Fdisk -l i get this:
```

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadd0add0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe42fe42f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2437    19575171    7  HPFS/NTFS

```

Tanks
Emanuel Teixeira

---

### Post by logos34 on 2007-11-02
Open menu.lst as root:

gksudo gedit /boot/grub/menu.lst

Add this to bottom:
> 
title		Windows XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

/boot/grub/device.map should also have a line for second drive:

> (hd1) /dev/hdb 

---

### Post by eteixeira on 2007-11-03
It worked like a charm !

Tank you !

---

