---
title: "Tryin to dual boot with XP sp2"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by GoBeavs956 on 2007-02-07
I am trying to get my PC to dual boot with Ubuntu on a IDE master hd and XP on a Sata hd.  The BIOS on my mobo will not allow me to boot from a SATA drive, so I must boot from the IDE.

When I try to boot XP, I get some messages that I do not understand:

root (hd1,0)

filesystem type unknown partition type 0x7

savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	(hd1,0) +1

Error 1:  Filename must be either an absolute or blocklist

Since I know that you guys will ask for it, here's what's in my grub:

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	(hd1,0) +1
boot


Does is make a difference that XP is on a SATA drive?  Any help would be wonderful (I'm jonsing to play WoW!!!!!).  

Thanks in advance,

Ty

---

### Post by mikewhatever on 2007-02-07
Hi, 
the Windows part of the menu should look like this
> title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

There is a [Good Guide]("http://www.ubuntuforums.org/showthread.php?t=179902") on this you may want to bookmark.

---

### Post by GoBeavs956 on 2007-02-07
Thanks Mikewhatever,

I was messing around with my grub and trying to get lucky.  Of course, remming those lines did nothing.  

I appreciate the help,

Ty

---

