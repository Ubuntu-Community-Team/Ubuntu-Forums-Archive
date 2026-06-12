---
title: "Software raid-1 /boot = black screen of death?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by oboontoo on 2008-04-28
I've done a fresh install of 8.04 alternate AMD64 on my machine that used to run Gutsy, but it now fails to boot. I don't even seem to get grub loaded. I have looked around for solutions, but I'm not sure what to look for.

I have 4 disks each with the same layout (only showing sda here)
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sda2              13         134      979965   fd  Linux raid autodetect
/dev/sda3             135         377     1951897+  fd  Linux raid autodetect
/dev/sda4             378        9039    69577515    5  Extended
/dev/sda5             378         863     3903763+  fd  Linux raid autodetect
/dev/sda6             864        9039    65673688+  fd  Linux raid autodetect
```

/etc/mdadm/mdadm.conf
```
...
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=b74ddbed:6bb465f7:26e478b8:2bfd4bf5
ARRAY /dev/md1 level=raid0 num-devices=4 UUID=dbe3e79c:75545076:93dc4dae:efc256c1
ARRAY /dev/md2 level=raid0 num-devices=4 UUID=f81ea7dd:b0b25441:377fc90c:6e2cd414
ARRAY /dev/md3 level=raid5 num-devices=4 UUID=5df8ac99:3b3773b1:0eb6a92a:5c415547
ARRAY /dev/md4 level=raid5 num-devices=4 UUID=6495f518:e4ca84fc:3557b24a:406b19c5

```

/etc/fstab
```
proc            /proc           proc    defaults        0       0
# /dev/md3
UUID=2d0ef2f8-2747-4506-9cfa-f656960d2432 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md0
UUID=1617617d-efcd-485e-918b-794fab08c325 /boot           ext3    relatime        0       2
# /dev/md4
UUID=3a4a3b6a-26ee-4ce8-bbca-6b46d01336c8 /data           ext3    noatime,relatime 0       2
# /dev/md2
UUID=b32085ee-e9ca-4929-8e67-a755cb4809c8 /tmp            ext3    noatime,relatime 0       2
# /dev/md1
UUID=cae4963d-4109-442f-80b2-9fcb2076fbc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

/boot/grub/menu.lst
```
...
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/md3 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet
...
```

I can boot in rescue mode from CD with /dev/md3 as root, then remount all my partitions with ```
mount -a
``` and then launch gdm (though there's a problem with initializing HAL) to get x going.

If I run find inside grub it doesn't find anything (isn't it supposed to)?
```
>find /sbin/init
file not found
>find /boot/grub/stage1
file not found
>find /boot/grub/stage2
file not found
```

Why isn't grub loaded? Did the installer fail to install grub into the MBR?

Martin

---

### Post by oboontoo on 2008-04-29
It appears that the Ubuntu installer installed grub into /dev/sda but this was obviously not the hard drive the bios tries to load the MBR from.

I got my ubuntu running by using rescue mode from the CD and then getting a shell up and running in my root partition /dev/md3 and then:```
grub-install /dev/sda
grub-install /dev/sdb
grub-install /dev/sdc
grub-install /dev/sdd
```

All is good:)

---

