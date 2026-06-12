---
title: "grub: windows doesn't boot, ubuntu in raid1"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by fedesuarez on 2008-05-14
Hi everybody,

I have three identical HD, first two (sda and sdb) are running software raid1 and the third is running windows. After installing Ubuntu server 8.04 (and then ubuntu-desktop on it) I install grub but when I restart and select to boot up windows I get this message:

Error 13
Invalid or unsupported executable format

I first installed Windows and then moved it to the last SATA connector and installed Ubuntu in the other two hd. Since there is no way to boot windows from grub, I connect only the windows HD and it boots normally.

I was googling a lot but couldn't find the solution for my setup... I have several partitions, here you go my fstab file:

```
# /dev/md5
UUID=30872970-1837-4310-9fdb-808cefa39ba8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md0
UUID=fed54234-927f-4c4e-91e3-aba0814109cf /boot           ext3    relatime        0       2
# /dev/md2
UUID=ca4c0b23-790c-443b-9229-3bde3d4fee7f /home           ext3    relatime        0       2
# /dev/md3
UUID=ce230ffd-e60a-41bb-87ee-0b28add96b15 /tmp            ext3    relatime        0       2
# /dev/md4
UUID=e9d64782-55e1-45e7-96ad-32b9ef771e47 /var            ext3    relatime        0       2
# /dev/md1
UUID=72e50e00-b317-40c8-8968-7dd8b528b7d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```


And the menu.lst file is this:

everything commented up to here...
## ## End Default Options ##

```
title		Ubuntu 8.04, kernel 2.6.24-16-server
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-server root=/dev/md5 ro quiet splash
initrd		/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-server root=/dev/md5 ro single
initrd		/initrd.img-2.6.24-16-server

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```



Besides that, I found some comments to make both raid disks bootable but they don't work... I suppose because of my /boot partition... this is what I should type:

```
mount /dev/md0 /mnt   #I don't do this
chroot /mnt           #I do chroot /boot but I have no sh!!!
grub
device (hd0) /dev/sda  #this doesn't work either... device doesn't exist.
root(hd0,0)
setup(hd0)
device(hd1) /dev/sdb
root(hd1,0)
setup(hd1)
quit
```


Ok, that's it up to now. Hope someone can help me!!!! Thanks a lot.

fede.

---

### Post by fedesuarez on 2008-05-14
Ok... I found the problem about booting with the HD running windows. I fixed it with a win98 boot disk and typing the magic words: fdisk /mbr. So, grub configuration was ok.

I think that a possible explanation to the problem is that somehow, the first time I tried to install X on ubuntu server everything crashed and corrupted my disks... that time I did: apt-get install x-window-system-core xserver-xorg gnome-core. (instead of apt-get install ubuntu-desktop) 
It seems that it couldn't managed the raid and ubuntu didn't boot anymore, so I re-installed everything but the HD running windows got any problem in the mbr.

Well, I'm still wondering how to boot up my raid with any disk... Can someone help me?

fede.

---

