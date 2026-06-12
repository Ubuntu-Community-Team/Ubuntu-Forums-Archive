---
title: "GRUB: Cannot boot Win 2000"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by Juggernaut on 2005-07-18
Hello, I am quite new to Ubunte and I must say that  it's one of the best Linuxes I've tried so far.

Well, the thing is that I can't get GRUB to boot my Win2000 partition.
I've searched the forum, but couldn't find an answer to my problem.

During installation, GRUB detected the Win2000 partition and I thought everything was just fine.
However, I can't boot to it. It says "filesystem type unknown, partition type 0x7"


My menu.lst:

```
#... COMMENTS REMOVED ...

default         0

timeout         10

#hiddenmenu

# Pretty colours
#color cyan/blue white/blue


title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdg1
title           Microsoft Windows 2000 Professional
rootnoverify            (hd2,0)
savedefault
makeactive
chainloader     +1
```



And here's what fdisk -l says (I had to translate it, hope it's ok):
```

device /dev/hda: 20.4 GByte, 20409532416 Byte
255 heads, 63 sectors/tracks, 2481 cylinders


  device   boot.  Beginning End     Blocks   Id  System
/dev/hda1   *           1           2       16033+  83  Linux
/dev/hda2               3          65      506047+  82  Linux Swap / Solaris
/dev/hda3              66        2481    19406520   83  Linux

device /dev/hdb: 40.0 GByte, 40020664832 Byte
255 heads, 63 sectors/tracks, 4865 cylinders

  device   boot.  Beginning End     Blocks   Id  System
/dev/hdb1               1        4864    39070048+   c  W95 FAT32 (LBA)

device /dev/hdg: 160.0 GByte, 160041885696 Byte
255 heads, 63 sectors/tracks, 19457 cylinders


  device   boot.  Beginning End     Blocks   Id  System
/dev/hdg1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hdg2            1021       11219    81923467+   f  W95 Erw. (LBA)
/dev/hdg5            1021       11219    81923436    b  W95 FAT32

```


So GRUB obviously translates /dev/hdg1 to hd2,0
But I still can't boot to that device.

If I choose to boot from the Windows drive in the Bios, I can boot into Windows, but if I decide to boot from the Linux drive with GRUB in the MBR, Windows is not an option, although it's listed. :  ](*,) 


Any suggestions are highly appreciated!

---

### Post by al7kz on 2005-07-18
Hi juggernaut,

This is a pretty common problem, trying for grub to boot windoze when it isn't on the first hard drive. Windoze needs to think it's on the first drive for some reason. Try remapping the drives in the grub menu, so the windoze entry would be:

title windoze
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

Ciao, al7kz

---

### Post by WildTangent on 2005-07-19
uh huh, always keep in mind that windows always thinks its number 1, and no one else exists ;)

-Wild

---

### Post by Juggernaut on 2005-07-19
Thanks for your fast responses! It's working now, great!!!

---

