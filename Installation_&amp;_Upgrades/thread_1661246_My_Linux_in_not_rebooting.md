---
title: "My Linux in not rebooting"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by hsharma121 on 2011-01-06
Hi 

When i start my system i get this error:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)

I have followed all the discussions that can be found from the links suggested by google search but I am not able to fix it. So it will be great if someone can help me.

I am posting the output of all the command that people asked in other discussion forums.

sudo fdisk -l```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed775c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     1998848   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         249       13055   102858752   83  Linux
/dev/sda3           13055       26109   104857600    6  FAT16
/dev/sda4           26109       38914   102853632    7  HPFS/NTFS

```

dmesg | tail

```
[   97.086392] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   97.086760] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   97.087113] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   97.405567] lp0: using parport0 (interrupt-driven).
[  105.848516] eth0: no IPv6 routers present
[  109.516342] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[  109.517971] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[  173.328684] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 1
[  174.772871] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[  174.774403] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1

```

```
ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda2
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?
```


Thanks !!
Himanshu

---

### Post by presence1960 on 2011-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by hsharma121 on 2011-01-06
Hi:

Following is the output after few minutes. I am sure it should not take that long.

Thanks!

```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
```

---

