---
title: "Yet Another Fiesty Grub Dual Boot Problem"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by toallpointswest on 2007-06-04
Hey all, 

My system has a bit of an odd config which isn't helping grub any: 

All drives are sata, except by cdrom drives with the following layout

sata (sda) = data
sata (sdb) = Ubuntu 7.0.4 Feisty
sata (sdc) = Windows XP

After the initial install of Ubuntu, there was no Grub menu present. So I booted the LiveCD and did the following: 

sudo'd to root
grub
root (hd2,0)
setup (hd2) 
quit

After which point, still nothing. No menu, and the machine boots straight into Windows. What else can I try?

---

### Post by merlinus on 2007-06-04
Try this:
```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute results from find in the next two commands.

Good luck!

-merlin

---

### Post by bulldog on 2007-06-04
> **toallpointswest said:**
> Hey all, 

My system has a bit of an odd config which isn't helping grub any: 

All drives are sata, except by cdrom drives with the following layout

sata (sda) = data
sata (sdb) = Ubuntu 7.0.4 Feisty
sata (sdc) = Windows XP

After the initial install of Ubuntu, there was no Grub menu present. So I booted the LiveCD and did the following: 

sudo'd to root
grub
root (hd2,0)
setup (hd2) 
quit

After which point, still nothing. No menu, and the machine boots straight into Windows. What else can I try?

The question should be,from which hdd are you booting?
By default GRUB is installed to sda,which is hd0,you installed it on sdc,which is hd2,so if you boot from sdb it's quit obvious you won't see any GRUB menu.:D

---

### Post by toallpointswest on 2007-06-04
> **bulldog said:**
> The question should be,from which hdd are you booting?
By default GRUB is installed to sda,which is hd0,you installed it on sdc,which is hd2,so if you boot from sdb it's quit obvious you won't see any GRUB menu.:D

I should be booting for hdc, as that's where Windows is.

---

### Post by toallpointswest on 2007-06-04
> **merlinus said:**
> Try this:
```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute results from find in the next two commands.

Good luck!

-merlin

Okay, tried that off the LiveCD and recieved:
```

grub> find boot/grub/stage1

Error 15: File not found

grub> find /mnt2/boot/grub/stage1

Error 15: File not found

grub>


```

The first try was before I mounted sdb1 as mnt2

EDIT: More info

Okay, in the /boot/grub directory I viewed menu.1st and device map and they are as follows: 

```

title           Ubuntu, kernel 2.6.20-15-server
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-server root=UUID=b6305a25-8a9e-45df-8e1a
-36c295a01c6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-server
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-server (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-server root=UUID=b6305a25-8a9e-45df-8e1a
-36c295a01c6a ro single
initrd          /boot/initrd.img-2.6.20-15-server

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b6305a25-8a9e-45df-8e1
a-36c295a01c6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
</snip>
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1


```

Then devices:

```

root@ubuntu:/mnt2/boot/grub# cat device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc


```

---

