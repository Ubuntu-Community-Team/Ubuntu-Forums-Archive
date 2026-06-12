---
title: "Grub error 17"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by jus1haz2 on 2008-08-09
I am getting Error 17 when i try and boot my system. I have windows installed on a 74GB drive and ubunut on the second partition of an 80GB drive.

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
16 heads, 63 sectors/track, 155009 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x49f2340b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       94452    47603304    f  W95 Ext'd (LBA)
/dev/sda2   *       94453      155009    30520728   83  Linux
/dev/sda5               2       91756    46244488+   7  HPFS/NTFS
/dev/sda6           91757       94452     1358752+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x060f173b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0000aba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      568168   286356640+   7  HPFS/NTFS

```

and here is my menu.lst

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829ce281-f889-43dc-ab0a-e100ab32ebc7 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829ce281-f889-43dc-ab0a-e100ab32ebc7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by Pumalite on 2008-08-09
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
(try changing the boot order in BIOS)

---

### Post by jus1haz2 on 2008-08-09
If I change it to boot from the 80Gb then I get Error 17 but if I change it to boot from the 74Gb then it goes straight into windows. 

Is grub just installed on the wrong drive?

---

### Post by Pumalite on 2008-08-09
Maybe. Do you have a mix of SATA and IDE? If that's the case; search in the Forum: Dualboot Two Hard Drives

---

### Post by jus1haz2 on 2008-08-09
I am going to just re-install ubuntu but use the entire 80GB this time, hopefully that fixes it.

---

