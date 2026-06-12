---
title: "booting or grub problem"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by abetterlie on 2008-02-25
Hello, 
I have a box with a mdadm array in it and a boot drive. I was trying to put some new drives  and controllers in, and after, the box wouldnt boot. I took the new drives and the controllers out, and it still wouldnt boot. I end up at a busybox prompt, because linux cannot find the image file to boot from. To remedy this temporarily, I installed another installation of linux on some unused space on the boot drive, and it boots fine. What I would like to do is either use this to get my original installation working (then put in the new drives) or migrate all my old users, samba settings, everything else to this 'new' installation. can anyone help? Obviously I would prefer to get the original installation working. 

here is where I get dumped: 
[IMG]http://img244.imageshack.us/img244/4550/screenjr0.jpg[/IMG]
Here are all the files that i think are pertinent:
```
root@indifferent:~# fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e527dbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       17512   140665108+  83  Linux
/dev/sda2           17513       17784     2184840    5  Extended
/dev/sda3   *       17785       18241     3670852+  83  Linux
/dev/sda5           17513       17755     1951866   82  Linux swap / Solaris
/dev/sda6           17756       17784      232911   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e0f3187

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ec0f8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12e84b44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

```

```
title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=c85dce0d-8f2d-48b2-aeec-d9af894f0f76 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=c85dce0d-8f2d-48b2-aeec-d9af894f0f76 ro single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-server (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c ro single
initrd          /boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot


```

Please help, I really would like to have this system back up, and the new drives installed...
Thanks!
matt.

---

### Post by dstew on 2008-02-25
It seems that you were trying to mount /dev/sda1 to the mount point "/root" but this mount point doesn't exist. From the next statement in the kernel messages, it seems that you may have confused "/root" with "/" (root). That is, when the kernel trys to mount /sys and /proc, it is trying to mount them to /root/sys and /root/proc, but those mount points do not exist.

Maybe there is something I don't understand about the RAID setup you have, but it seems that the root file system may not have been designated properly.

---

### Post by abetterlie on 2008-02-25
I wonder how that got messed up? any idea on how to point it to '/' ? where would I change this?
also, from the intramfs if i type mount, it does not show sda1 to be mounted at all... 

the system still does not boot, and in the meantime I have tried fsck.ext3, which came back without errors... 
I also was wondering if blkid might have anything to do with it.

---

### Post by dstew on 2008-02-25
I assume /dev/sda1 is your original Linux installation, and that /dev/sda3 contains your "rescue" installation. I also assume you get these errors when you choose the grub menu item with the title "Ubuntu 7.10, kernel 2.6.22-14-server (on /dev/sda1)" Just to make sure we know which disks are which, from your rescue linux install terminal, enter```
vol_id -l /dev/sda1
```Do this for /dev/sda1 and /dev/sda3, and post the results.
EDIT: One more thing. Can you mount your /dev/sda1 file system onto your /dev/sda3 file system? If you make a mountpoint of /mnt/sda1 and try ```
sudo mount -t ext3 /mnt/sda1
```I would like to see the fstab file in there:```
cat /mnt/sda1/etc/fstab
```If the partition cannot be mounted, post the error.

---

### Post by abetterlie on 2008-02-25
the command vol_id -l /dev/sda1 or sda3 does not output anything as the volumes are identified by UUID only. 

```
root@indifferent:~# vol_id -u /dev/sda1
be715b50-69e2-48ac-8de2-a2fb4862c46c
root@indifferent:~# vol_id -u /dev/sda3
c85dce0d-8f2d-48b2-aeec-d9af894f0f76
root@indifferent:~#

```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c85dce0d-8f2d-48b2-aeec-d9af894f0f76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=df2bc05a-cb4e-4987-bd54-30e7ec52baec none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

everything appears to be consistent with fstab, menu.lst. 

Also, there is a /root dir
drwxr-xr-x  2 root root  4096 2008-02-25 10:10 root

Thanks for your help so far...

---

### Post by dstew on 2008-02-25
OK, that is good. But see my edit. I would like to see the fstab in your original linux install, since that is where the errors come from. Your fstab in your /dev/sda3 parition seems fine, and the UUIDs are OK.

Looking at the errors, it seems that when you boot the /dev/sda1 system, it tries to mount the be715 partition onto /root. Since that parition is already mounted on / (or at least should be) it is busy, and that command fails. Since there is nothing mounted on /root because of that error, the other mount commands also fail because the mountpoints in /root do not exist.

EDIT: That is a pretty impressive RAID, 3 Tb

---

### Post by abetterlie on 2008-02-25
everything looks good in this fstab too i think.
I think I understand what you are saying, that would explain why the device is busy...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7457f78e-3d6a-4343-a485-efa3b8b1c949 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/md0  /var/swaproot/  ext3  user,suid,dev,exec  0  0
/dev/sda1 /mnt/USB auto noauto,owner,kuzu 0 0

@RAID: were actually trying to turn this into a 7tb raid, that is where this boot problem stemmed from, after the controllers went in, something went wrong. once this gets sorted, I am going to attempt that again.

---

### Post by dstew on 2008-02-25
I noticed this:```
/dev/sda1 /mnt/USB auto noauto,owner,kuzu 0 0
```Not sure if that is part of the problem, though. Do you have a USB drive plugged in? If so, could that be a cause of the unusual mount commands?

Anyway, the fstab looks generally OK. But some process is trying to mount the root file system, and others, to /root, and failing. It looks like it is a script local-premount that issues the first mount command, and other scripts issue the others. I don't know a lot about the scripts though, and how to debug this further. It might be good to see the kernel log file in your /dev/sda1 /var/log directory. I guess I want to get a feel for the context in which those errors occur.

---

### Post by abetterlie on 2008-02-25
There is no USB drive plugged in, in a flash of hope, I removed that line and rebooted, had no effect. sharp eyes though, Ive stared at that file for so long i stopped seeing that one. 
where do I go to enable and disable those scripts? Can I just comment them out somewhere? 

There wasant really anything interesting in the kernel log, just a whole bunch of errors concerning eth0:

Feb 22 16:23:34 indifferent kernel: [1298863.793485] eth0: too many iterations (6) in nv_nic_irq.
Feb 22 16:23:34 indifferent kernel: [1298863.862442] eth0: too many iterations (6) in nv_nic_irq.
Feb 22 16:23:34 indifferent kernel: [1298864.055616] eth0: too many iterations (6) in nv_nic_irq.
Feb 22 16:23:38 indifferent kernel: [1298867.426647] eth0: too many iterations (6) in nv_nic_irq.
Feb 22 16:29:44 indifferent kernel: Kernel logging (proc) stopped.
Feb 22 16:29:44 indifferent kernel: Kernel log daemon terminating.

sorry for my ignorance, but where are the bootlog files stored? maybe there would be a clue there...

---

### Post by abetterlie on 2008-02-25
anyone else want to take a swing?

---

### Post by dstew on 2008-02-25
> where do I go to enable and disable those scripts? Can I just comment them out somewhere?I don't know a lot about scripts, only that they are run during the initialization of the system. See the [init man page]("http://linux.die.net/man/8/init"). Init is the program that runs most of the scripts. It is run from /sbin/init. In your error message, the kernel cannot find that directory, so the boot fails. I guess the local-premount script is run directly by the kernel after it first loads. So, really, the system never even gets off the ground. I also see errors higher up. It would be nice to look at all of them. So maybe post the whole dmesg log.

Could there be file-system corruption? Try sudo fsck -a /dev/sda1

---

### Post by abetterlie on 2008-02-26
I tried the fsck -a on the system drive, but it checked out ok...

I gave up and reinstalled. users are going to be super pissed, and have to make all thier passwords again, but I really couldnt find a faster way to fix this. Thanks for all your help.

---

