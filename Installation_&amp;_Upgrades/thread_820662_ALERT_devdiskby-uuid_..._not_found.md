---
title: "ALERT: /dev/disk/by-uuid ... not found"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by jgauthier on 2008-06-06
All,

  I've seen this a few times here with varying solutions and successes.  In short, I customized my kernel using the "Ubuntu Way".

This was not new to me, because I've been using debian for years.
Upon reboot, I received the dreaded "ALERT: /dev/disk/by-uuid XXXXXX not found".

From the built in shell, I've discovered that /dev/disk does not even exist.  Did I totally miss something in the kernel compilation?  I did base this off the running/functioning kernel.

Thanks for ideas.

---

### Post by PmDematagoda on 2008-06-06
Post the outputs of:-
```
cat /boot/grub/menu.lst
```
and
```
sudo blkid
```

---

### Post by jgauthier on 2008-06-06
cat /boot/grub/menu.lst:
```

(without comments):
default         0
timeout         10
title           Ubuntu 8.04, kernel 2.6.25.4-mythtv1
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.25.4-mythtv1 root=UUID=c2f6b704-33c2-4431-8ed4
-dca303d3a627 ro quiet splash
initrd          /boot/initrd.img-2.6.25.4-mythtv1
quiet

title           Ubuntu 8.04, kernel 2.6.25.4-mythtv1 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.25.4-mythtv1 root=UUID=c2f6b704-33c2-4431-8ed4
-dca303d3a627 ro single
initrd          /boot/initrd.img-2.6.25.4-mythtv1

title           Ubuntu 8.04, kernel 2.6.24-18-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=c2f6b704-33c2-4431-8ed
4-dca303d3a627 ro quiet splash
initrd          /boot/initrd.img-2.6.24-18-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=c2f6b704-33c2-4431-8ed
4-dca303d3a627 ro single
initrd          /boot/initrd.img-2.6.24-18-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c2f6b704-33c2-4431-8ed
4-dca303d3a627 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c2f6b704-33c2-4431-8ed
4-dca303d3a627 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet


title           Other operating systems:
root


title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```
and sudo blkid
```

/dev/sda1: UUID="B42807012806C1FA" TYPE="ntfs"
/dev/sda2: TYPE="swap" UUID="d7c5ca8b-15c3-4e90-8b5f-721e7e169ccc"
/dev/sda3: UUID="c2f6b704-33c2-4431-8ed4-dca303d3a627" TYPE="ext3"

```

---

