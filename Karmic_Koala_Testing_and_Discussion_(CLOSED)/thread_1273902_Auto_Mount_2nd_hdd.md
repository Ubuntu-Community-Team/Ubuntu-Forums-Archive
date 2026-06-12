---
title: "Auto Mount 2nd hdd"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-09-23
Is there an easy way to set it up so that my second hdd automounts on boot.  You would think that ubuntu would do this by default...

---

### Post by nhasian on 2009-09-23
my laptop has two hard disks in it.  ubuntu is my only operating system.  I partitioned the entire 2nd hard disk as EXT4 and set it as /data.  You can either set it during the installation process, or afterwards by editing /etc/fstab

---

### Post by keenish27 on 2009-09-23
ugh...so I still have to edit the fstab....You would think by nice there would be an easy way =P

Oh wells.  Thanks.

---

### Post by nhasian on 2009-09-23
its not hard at all.  here's my /etc/fstab if you'd like to use it as an example:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=891e9ea8-8d6d-4254-b8b4-583181463ef8 /               ext4    relatime,errors=remount-ro 0       1
# /data was on /dev/sdb1 during installation
UUID=35dc8f8c-8f88-4e2e-8b4a-22138aea0e88 /data           ext4    relatime        0       2
# /home was on /dev/sda3 during installation
UUID=abe8084b-3d5e-45df-93cc-3a6ac2ca68f0 /home           ext4    relatime        0       2
# swap was on /dev/sda4 during installation
UUID=df3c1e89-54ba-4eae-8b3e-33a17b40de4e none            swap    sw              0       0


---

