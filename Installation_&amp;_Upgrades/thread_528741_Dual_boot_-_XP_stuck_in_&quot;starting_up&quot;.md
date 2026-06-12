---
title: "Dual boot - XP stuck in &quot;starting up&quot;"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Fl3tchLiv3s on 2007-08-18
Hi, I'm trying to get windows XP and Ubuntu to dual boot on my PC. 

Here's what I did:
I installed XP on the SATA drive (has been like that for months and don't want to change). 
I Disconnected the SATA and changed to boot from the IDE in the BIOS then installed Ubuntu on the IDE drive. 
I then changed the device.map and menu.lst to try and allow me to choose windows or Ubuntu from GRUB when the BIOS is set to boot from the IDE. 

Ubuntu is loading fine but XP gets stuck on "Starting up...". If I change to boot from the SATA drive then XP boots fine as normal.
Can anyone suggest how I need to change my GRUB setup so this works? 
I was up till 3am trying to figure this out and i've looked through lots of forums but i've not found anyone else that seems to have got it to work that's had the same problem.
I originally tried to use the install with the SATA drive in but the GRUB Loader seemed to have trouble even starting hence me trying to set it up manually.

Here's some info:

menu.lst ->>
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42d63176-6760-4024-9e5c-c2c6a5d0d332 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42d63176-6760-4024-9e5c-c2c6a5d0d332 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


title           Windows XP Professional SP2
root            (hd2,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd2)
map (hd2) (hd0)

device.map ->>

(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)   /dev/sda

sudo fdisk -lu ->>

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    74878964    37439451   83  Linux
/dev/hda2        74878965    78172289     1646662+   5  Extended
/dev/hda5        74879028    78172289     1646631   82  Linux swap / Solaris

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   320159384   160079661    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS


Any suggestions would be appreciated.
Cheers,
Andy

---

### Post by confused57 on 2007-08-18
You could try rootnoverify, instead of root & try removing the savedefault line:
```
title Windows XP Professional SP2
rootnoverify (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
depending on your bios boot sequence options, try to have the boot order set up the same as your device.map(hda,hdc,sda).

If it still doesn't work and you can set sda  to boot next after hda in bios, then try changing your device.map and your Window's grub entry to (hd1,0) with the map lines changed accordingly.

---

