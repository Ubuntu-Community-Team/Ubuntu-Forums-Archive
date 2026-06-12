---
title: "Urgent help needed please - Grub installtion"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by El Duke on 2010-01-14
Hi, 


I have this weird problem. The other day I asked a question about restore the backup file after dual boot installation. I have done the dual boot ( XP installed first) then restored the backup file. 


Now the problem is that I forgot if I excluded system files from backup or not, so when I restored and rebooted, my installations got messed up, many programs do not find their path to run, etc.. 


But the real problem is when I rebooted again, I got **error 15: file not found**


tried to follow some other posts here to solve this and noticed that running fdisk -l gives me:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       19457    84606322+   f  W95 Ext'd (LBA)
/dev/sda5            8925       10199    10241406    7  HPFS/NTFS
/dev/sda6           10200       12065    14988613+   7  HPFS/NTFS
/dev/sda7           12066       19150    56910231   83  Linux
/dev/sda8           19151       19457     2465946   82  Linux swap / Solaris

Disk /dev/sdb: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xd2cee7c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16        7656     1955904    b  W95 FAT32

```
Plus, when I tried to browse partitions, I have noticed that I have two partitions with system files in. one in which I installed last ubuntu, and the other is the restored one, so now I am confused which is my real boot device, how to re-install grub in this case ?



P.S. I am also confused which is the real menu.ls file, I have 2, the first one from which I see the boot menu now and it contains this:

```
title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2815c1b9-1764-4ab5-ab29-1689fb2d975b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2815c1b9-1764-4ab5-ab29-1689fb2d975b
kernel        /boot/memtest86+.bin
quiet
```

The other is the old messed one ( this one is not contained in a folder called grub, it is just in the boot folder:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8ed03294-2ef3-45b8-aaa5-1687dfd1b340
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8ed03294-2ef3-45b8-aaa5-1687dfd1b340 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8ed03294-2ef3-45b8-aaa5-1687dfd1b340
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8ed03294-2ef3-45b8-aaa5-1687dfd1b340 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8ed03294-2ef3-45b8-aaa5-1687dfd1b340
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```


Please help ASAP as I am planning to go on a photography trip and I need my laptop with me :(


Thanks

---

### Post by dstew on 2010-01-14
When you boot the computer, do you get a grub menu, or just the error message?

---

