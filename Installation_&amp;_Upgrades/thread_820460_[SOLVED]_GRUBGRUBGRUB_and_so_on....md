---
title: "[SOLVED] GRUBGRUBGRUB and so on..."
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by wapcaplit on 2008-06-06
Greetings...

I've inflicted some grief on myself today. I installed some new hardware (RAM and a 2nd GPU) - I had to move a SATA adapter to shoehorn the 2nd GPU in there. I suspect that this has reordered my HDDs. Just to maximise my own "wazzockry" I then installed vista x64. Mwuhahaha. I've attempted to compensate and reinstall grub, but all I get on boot is the old "GRUBGRUBGRUB" ad-infinitum.

Hoping someone out there can offer some sage advice.

Here's my disk config as reported by the 8.04 amd64 live CD:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06e9019e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4570e119

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5be78269

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x913531f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91719eae

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044930

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ead9ead

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdh: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033ee9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        4177    33551721   83  Linux
/dev/sdh2            4178        9039    39054015    5  Extended
/dev/sdh5            4178        9039    39053983+  82  Linux swap / Solaris

Disk /dev/sdi: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90fe90fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       19457   156288321   fd  Linux raid autodetect

```

Vista is on sdf1. Ubuntu 8.04 amd64 is on sdh1.

My device.map (from sdh1) looks like this (I rebuilt this today by moving the old device.map and running grub --device-map=blah):

```

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf
(hd6)	/dev/sdg
(hd7)	/dev/sdh
(hd8)	/dev/sdi

```

My menu.list looks as follows. I mod'd this today as well, changing the hd2 to hd7 for the linux images and from hd0 to hd5 for the wintel image.

```

root@ubuntu:/boot/grub# egrep -v '^#|^$' menu.lst
default		0
timeout		10
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro single
initrd		/boot/initrd.img-2.6.24-18-generic
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro single
initrd		/boot/initrd.img-2.6.24-17-generic
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd7,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
title		Ubuntu 8.04, memtest86+
root		(hd7,0)
kernel		/boot/memtest86+.bin
quiet
title		Other operating systems:
root
title		Microsoft Windows XP Professional
root		(hd5,0)
savedefault
chainloader	+1

```

From a grub shell I can find /boot/grub/stage1 no probs on (hd7,0) as I'd expect. I've been running a setup onto (hd5), i.e. the Vista disk's MBR - this is the config I was using before (i.e. when I had XP32 on that partition).

I've also tried the old mount of sdh1 onto /mnt, also mounting proc and dev as follows:

```

root@ubuntu:~# mount /dev/sdh1 /mnt/root
root@ubuntu:~# mount -t proc none /mnt/root/proc
root@ubuntu:~# mount -o bind /dev /mnt/root/dev
root@ubuntu:~# chroot /mnt/root /bin/bash
root@ubuntu:/# cd /boot/grub
root@ubuntu:/boot/grub# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd7,0)
grub> root (hd7,0)
root (hd7,0)
grub> setup (hd5)
setup (hd5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd5)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd5) (hd5)1+16 p (hd7,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
root@ubuntu:/boot/grub# sync;sync;sync

```


I seem to be getting the same result each time...flipping GRUBGRUBGRUB...

In the "pre-wazzockry" grub config the drives sda to sde weren't in the picture...I had a simple, happy grub in which hd[0-3] mapped to sd[a-d] and the 5 drives (which are now reported as sd[a-e]) hanging off the sata adapter didn't get a look in sideways.

Anyone got any good suggestions? I'm open to the idea of undoing all my changes, but in the spirit of forging ahead to find the really deep quicksand I'd appreciate any clever ideas as to resolving this.

TIA

Wapcaplit, Adrian Wapcaplit.

---

### Post by wapcaplit on 2008-06-06
Heheh I fixed the *&£^$*£.

Moving the pci SATA adapter between slots caused the BIOS to add those disks into the boot list. Previously they weren't present.

A simple re-ordering of the device.map did the trick.

---

