---
title: "Add ubuntu entry to boot menu"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by elaich1988 on 2010-04-02
Hi all,
i just installed ubuntu 9.10 netbook remix, i made a partition (sda6) for it, first i had only opensuse, and when i was installing ubuntu, i put the bootloader in (sda6) the Opensuse bootloader is installed on MBR, 
```
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb02fb02f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          14      112423+  83  Linux
/dev/sda2              15       19457   156175897+   f  W95 Ext'd (LBA)
/dev/sda5              15         275     2096451   82  Linux swap / Solaris
/dev/sda6             276        1580    10482381   83  Linux
/dev/sda7            1581        2885    10482381   83  Linux
/dev/sda8            2886        4190    10482381   83  Linux
/dev/sda9            4191        6279    16779861   83  Linux
/dev/sda10           6280       19457   105852253+  83  Linux
```when i start the eeepc i have my opensuse grub screen, how can i add ubuntu to it ?

```
 # mount -t ext4 /dev/sda6 /ubuntu
# cd /ubuntu
# cd boot
/boot # ls -l
total 13760
-rw-r--r-- 1 root root  629174 2009-10-16 18:03 abi-2.6.31-14-generic
-rw-r--r-- 1 root root  111371 2009-10-16 18:03 config-2.6.31-14-generic
drwxr-xr-x 2 root root    4096 2010-04-02 01:27 grub
-rw-r--r-- 1 root root 7645067 2010-04-02 01:28 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root  128796 2009-10-23 16:11 memtest86+.bin
-rw-r--r-- 1 root root 1664737 2009-10-16 18:03 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root    1196 2009-10-16 18:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root 3890400 2009-10-16 18:03 vmlinuz-2.6.31-14-generic

```I hope somedbody can help !
thanks

---

### Post by oldfred on 2010-04-02
What boot loader does Opensuse use? grub legacy, grub2 or other?

If you managed to get grub2 into the Ubuntu partition (it does not like to do that, but I have), you can chainboot:

Grub2 entry:
menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1
}

Using old grub to chainboot:
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by elaich1988 on 2010-04-03
Suse uses grub, i have already add these lines to menu.lst
```
title ubuntu 9.10
root    (hd0,5)
chainloader +1

```

---

### Post by elaich1988 on 2010-04-03
But when i try to start with it i have only an error:
```
root (hd0,5)
File system type is ext2fs, partition type 0x83
chainloader +1
Error 13: invalid or unsupported executable format.
```

---

### Post by sisco311 on 2010-04-03
Grub2 includes a boot image that's loadable from Grub legacy:
```
title Ubuntu 9.10 Karmic Koala
root (hd0,5)
kernel /boot/grub/core.img
savedefault
boot

```

---

### Post by oldfred on 2010-04-03
Grub legacy (0.97) has not been mantained for years. Ubuntu updated their version to allow booting into ext4 partitions. Is your install of 9.10 using ext4?

---

