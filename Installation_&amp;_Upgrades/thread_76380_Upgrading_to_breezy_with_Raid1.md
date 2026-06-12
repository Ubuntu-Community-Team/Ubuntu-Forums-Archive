---
title: "Upgrading to breezy with Raid1"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by tincanman on 2005-10-15
I upgraded to breezy on a server that I am running with mdadm software Raid1. I am no longer able to boot off the raid.

My mdadm.conf file is as follows:

```
DEVICE /dev/hda1 /dev/hde1 /dev/hda3 /dev/hde3 /dev/hd4 /dev/hde4
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=0708ab62:a330ece8:8a0dc74f:a602dabc
   devices=/dev/hde4,/dev/hda4 auto=yes
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=5d4e9cbb:11855337:3cdab32b:73386524
   devices=/dev/hde3,/dev/hda3 auto=yes
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c451f4f8:902b7dae:b978c718:b29c6046
   devices=/dev/hde1,/dev/hda1 auto=yes
```

My root partition is on /dev/md1 and my boot partition on on /dev/md0.

My menu.lst file for grub is a follows:

```
title           Ubuntu, Raid HD0 kernel 2.6.12-9-686-smp
root            (hd0,0)
kernel          /vmlinuz-2.6.12-9-686-smp root=/dev/md1 ro quiet splash
initrd          /initrd.img-2.6.12-9-686-smp
savedefault
boot

``` 

Now with this configuration I was able to boot up wardy just fine... but after upgrading to breezy I get the following error on boot:

```
Loading Please wait...
mdadm: /dev/md0 has been started with 2 drives
mdadm: /dev/md1 has been started with 2 drives
mdadm: /dev/md2 has been started with 2 drives
FATAL: Module unknown not found
mount: Moutning /dev/md1 on /root failed: no such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on root/dev failed: No such file or directory
Target filesystem dosen't have /sbin/init
```

Then I get a prompt with busybox.

Now if I change my menu.lst to:

```
root            (hd0,0)
kernel          /vmlinuz-2.6.12-9-686-smp root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.12-9-686-smp
savedefault
boot
```

It boots just fine and my raids are started and running.

I also tried adding the following to /etc/mkinitrd/modules:

```
raid1
md
```

But get the same error as above.

Anyone have any ideas??? I am stumped on this one.

---

### Post by frey0814 on 2006-01-14
Did you ever solve this issue.  I have the same issue.  However, my raid device is a raid5 so I can't point root at one of the drives.

---

