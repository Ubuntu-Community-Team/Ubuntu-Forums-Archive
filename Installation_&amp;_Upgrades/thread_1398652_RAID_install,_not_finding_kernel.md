---
title: "RAID install, not finding kernel"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by theRemix on 2010-02-04
i have a gentoo install setup like this. 

i have 4 1TB disks, i used the fdisk utility to partition each identically, no special configuration. 

so now have 
```
/dev/sda1 /dev/sda2 /dev/sda3 /dev/sda5 /dev/sdd6 
/dev/sdb1 /dev/sdb2 /dev/sdb3 /dev/sdb5 /dev/sdd6 
/dev/sdc1 /dev/sdc2 /dev/sdc3 /dev/sdc5 /dev/sdd6 
/dev/sdd1 /dev/sdd2 /dev/sdd3 /dev/sdd5 /dev/sdd6 
```

and used mdadm like this 

```
mdadm --create --verbose /dev/md1 --level=1 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 
mdadm --create --verbose /dev/md2 --level=5 --raid-devices=4 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 
mdadm --create --verbose /dev/md3 --level=5 --raid-devices=4 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3 
mdadm --create --verbose /dev/md4 --level=5 --raid-devices=4 /dev/sda5 /dev/sdb5 /dev/sdc5 /dev/sdd5 
mdadm --create --verbose /dev/md5 --level=5 --raid-devices=4 /dev/sda6 /dev/sdb6 /dev/sdc6 /dev/sdd6 
```

works fine. 

my grub.conf 
```
title Gentoo 
root (hd0,0) 
kernel /boot/gentoo-2.6.31-r5 root=/dev/md3
```

In my kernel config, i enabled "autodetect RAID at boot" 
grub loads my kernel, then i get a kernel panic.
```
md: Autodetecting RAID arrays. 
md: Scanned 0 and added 0 devices. 
md: autorun ... DONE. 
VFS: Cannot open root device "md3" or unknown-block(0,0) 
Please append a correct "root=" boot option; here are the available partitions: 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

can someone help me?

tia

---

