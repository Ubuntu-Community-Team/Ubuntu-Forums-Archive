---
title: "dual boot 2 hard drives"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2007-03-06
Hi.  I could of sworn I submitted this thread a couple hours ago, but maybe i forgot to hit the submit key.. i couldn't find it anywhere, so if for some reason this shows up twice, i sincerely apologize..
I have 2 bootable hard drives, one ubuntu edgy, one fc6.  decided i would like to have them both in the same computer, and be able to select which distro to boot up.  i changed the pins on fc6 to make that hd a slave instead of primary, and installed the hd.  i boot into ubuntu, and mounted the secondary hd as hdb, and added it (can't remember, but i think it was) to the fstab.  anyway, when it boots up, the 2nd hd is mounted.
What do i need to do to make the 2nd hd (fc6 in this case) show up in the menu.lst (mbr?), so i can choose which distro boots, or which drive ?
i was hoping i would not have to repartition and reload the 2nd drive..
thanks for your help.

---

### Post by chewearn on 2007-03-07
> **vbdanl said:**
> 
What do i need to do to make the 2nd hd (fc6 in this case) show up in the menu.lst (mbr?), so i can choose which distro boots, or which drive ?
i was hoping i would not have to repartition and reload the 2nd drive..
thanks for your help.

To edit boot menu:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by vbdanl on 2007-03-07
thought i better ask before i make my computer unbootable..
Here is sudo fdisk -l
```
dan@Dan-linux-Antec:/boot/grub$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2389    19189611   83  Linux
/dev/hda2            2390        2482      747022+   5  Extended
/dev/hda5            2390        2482      746991   82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        4982    39913492+  8e  Linux LVM
```

The 2nd hd used to be a primary drive.  I changed the pins (made it slave, or at least I think I did) so I could have 2 drives, and hopefully could choose which drive to boot up.

Here is cat /etc/fstab
```
dan@Dan-linux-Antec:/boot/grub$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=928347b9-55ae-481d-b398-809fa7eb4d50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0aaf15f8-01c9-462c-b315-f7477ede3603 none            swap    sw              0       0
/dev/hdb1       /media/hd2        ext3   defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
dan@Dan-linux-Antec:/boot/grub$
```

df output
```
dan@Dan-linux-Antec:/boot/grub$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18888420   3929928  13999012  22% /
varrun                  127988        92    127896   1% /var/run
varlock                 127988         0    127988   0% /var/lock
procbususb               10240       152     10088   2% /proc/bus/usb
udev                     10240       152     10088   2% /dev
devshm                  127988         0    127988   0% /dev/shm
lrm                     127988     17580    110408  14% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1               101086     15689     80178  17% /media/hd2
dan@Dan-linux-Antec:/boot/grub$ 
```

Here is the last part of menu.lst
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro vga=791
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot
```

NOW - I was going to add this to menu.lst
I copied this from the fedora menu.lst.  changed the hd0,0 to hd1,0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu

title Fedora Core (2.6.18-1.2869.fc6)
        root (hd1,0)
        kernel /vmlinuz-2.6.18-1.2869.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.18-1.2869.fc6.img

title Fedora Core (2.6.18-1.2868.fc6)
        root (hd1,0)
        kernel /vmlinuz-2.6.18-1.2868.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.18-1.2868.fc6.img

Here is what I see when I ls -l /media/hd2
dan@Dan-linux-Antec:~$ cd /media/hd2
dan@Dan-linux-Antec:/media/hd2$ l
total 9842
-rw-r--r-- 1 root root   69381 2006-12-15 16:48 config-2.6.18-1.2868.fc6
-rw-r--r-- 1 root root   69512 2006-12-20 14:06 config-2.6.18-1.2869.fc6
drwxr-xr-x 2 root root    1024 2007-01-07 17:53 grub
-rw------- 1 root root 2176310 2006-12-26 21:54 initrd-2.6.18-1.2868.fc6.img
-rw------- 1 root root 2176246 2007-01-07 17:43 initrd-2.6.18-1.2869.fc6.img
drwx------ 2 root root   12288 2006-12-25 15:15 lost+found
-rw-r--r-- 1 root root   91993 2006-12-15 16:48 symvers-2.6.18-1.2868.fc6.gz
-rw-r--r-- 1 root root   91993 2006-12-20 14:06 symvers-2.6.18-1.2869.fc6.gz
-rw-r--r-- 1 root root  874975 2006-12-15 16:48 System.map-2.6.18-1.2868.fc6
-rw-r--r-- 1 root root  874975 2006-12-20 14:06 System.map-2.6.18-1.2869.fc6
-rw-r--r-- 1 root root 1786814 2006-12-15 16:48 vmlinuz-2.6.18-1.2868.fc6
-rw-r--r-- 1 root root 1786808 2006-12-20 14:06 vmlinuz-2.6.18-1.2869.fc6
dan@Dan-linux-Antec:/media/hd2$

I don't see the files you would normally see under "root".
I am guessing it is because I need to mount hdb2, but I am not sure if that will work.
I am also guessing what I have mounted from the second hard drive is just the boot partition, but I am not sure if that is what you call it.. or if that is even correct.
Can someone help me out here.. ?
Thanks.

---

### Post by confused57 on 2007-03-07
I've never used Fedora, but adding entries to the very end of your Ubuntu menu.lst won't hurt anything,   you could try your first entry:

title Fedora Core (2.6.18-1.2869.fc6)
root (hd1,0)
kernel /vmlinuz-2.6.18-1.2869.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /initrd-2.6.18-1.2869.fc6.img

and maybe a second entry:

title Fedora Core (2.6.18-1.2869.fc6) test2
root (hd1,0)
kernel /vmlinuz-2.6.18-1.2869.fc6 ro root=/dev/hdb1 rhgb quiet
initrd /initrd-2.6.18-1.2869.fc6.img

Being at the bottom of the menu.lst file won't affect your ability to boot Ubuntu...see if one of the entries will work.

---

