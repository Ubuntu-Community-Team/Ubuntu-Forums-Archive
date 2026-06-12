---
title: "GRUB with windows as second HD (SATA)"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by bklebel on 2007-02-07
Ok, I installed Ubuntu 64 last night and everything went great. During the process I disconnect my XP hard drive just to be safe.  Now that everything is running I want to setup GRUB to switch between my two harddrives. My Ubuntu is a 10 gig IDE and my XP is a 300 gig SATA (if that helps) In the BIOS my first HD in line is Ubuntu and second in line is my XP HD.  When I boot, it goes to GRUB but no Windows option. So I read the forums and followed some suggestions. I edited my /boot/grub/menu.lst a few different ways but still doesn't want to go.  I've read people have troubles when XP is the second in line.  I'll post some info for you guys. Please help

This is my menu.lst now:
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


title		Windows XP
root		(hd1,0)
map		(hd0)(hd1)
map		(hd1)(hd0)
savedefault
makeactive
chainloader+1




klebel@Ubuntu64:~$ sudo fdisk -lu

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   524650769   262325353+   7  HPFS/NTFS
/dev/sda2       524650770   586099394    30724312+   f  W95 Ext'd (LBA)
/dev/sda5       524650833   586099394    30724281    7  HPFS/NTFS

Disk /dev/hda: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633072 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    14924384     7462161   83  Linux
/dev/hda2        14924385    15631244      353430    5  Extended
/dev/hda5        14924448    15631244      353398+  82  Linux swap / Solaris

---

### Post by confused57 on 2007-02-07
I think you need to have a space between your mapping commands:

title Windows XP
root  (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader+1

See this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by bklebel on 2007-02-07
Ok I did that but now all it does when I hit enter on Windows XP is just flash and not go anywhere. I don't get any type of error or anything just sits there.

---

### Post by confused57 on 2007-02-07
I missed it the first time, but you also need a space between chainloader & +1:

chainloader +1

If that fails, try copy & pasting the Windows entry in the link I gave you to your menu.lst.

---

### Post by bklebel on 2007-02-07
You got it! your the man. Its always the little stuff that is always overlooked. Damn I wish I would of went to bed last night before 3!!

---

