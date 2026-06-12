---
title: "Partial upgrade"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by wwoollff on 2007-05-06
hi.Because I have a slow internet connection, I chose to upgrade my Edgy  to Feisty by upgrading file by file,because the normal upgrade had stopped(internet problem). After upgrading part of my system, I had to reboot my computer.When it rebooted, it simply froze during hardware mounting.It displays my network card name, then the hdd partitions, then it stoppes.It gives no error...nothing.
So, I would like to know how to get into the konsole to restore my system.The backup file is not damaged, but I simply don't now how to get to the konsole.

Thx.
P.S. I have tried recovery mode and I have no hardware problem because my Windows works fine

---

### Post by mlind on 2007-05-06
I think you're experiencing problem where feisty cannot find your root partition and just waits for the partition to mount. It should drop in to a busybox shell after some time.

Could you boot using the livecd, mount your root partition and post the output of
```

sudo fdisk -l

```

Also the first kernel entry in your /boot/grub/menu.lst

To chroot in to your current root partition using livecd
```

sudo mount /dev/xxx /mnt
sudo chroot /mnt

```
where /dev/xxx is the feisty root (/) partition, which you can find out from the output of fdisk -l

---

### Post by wwoollff on 2007-05-07
/boot/grub/menu.lst:
```

...
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.20-15-generic
boot
...

```

fdisk -l: 
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1215     9759456    7  HPFS/NTFS
/dev/hda2            1216        8254    56540767+   f  W95 Ext'd (LBA)
/dev/hda5            1216        5470    34178256    b  W95 FAT32
/dev/hda6            5471        8187    21824271    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       28938   211961610    f  W95 Ext'd (LBA)
/dev/sda3           28939       30401    11751547+  83  Linux
/dev/sda5            2551       15298   102398278+   7  HPFS/NTFS
/dev/sda6           15299       28871   109025091    7  HPFS/NTFS
/dev/sda7           28872       28938      538146   82  Linux swap / Solaris

```

---

### Post by mlind on 2007-05-07
Sorry I forgot, could you also post your /boot/grub/devices.map.

Grub probably sees your /dev/sda3 as /dev/hdb1. You should try using UUID though which you can get by using volume_id

```

sudo vol_id /dev/sda3 | grep UUID

```

Then open your /boot/grub/menu.lst file and replace
```

# kopt=root=/dev/sda3 ro

```
with
```

# kopt=root=UUID=xxxxxxxxxx ro

```
where x's are the UUID from vol_id output

Then update grub menu
```

sudo update-grub

```


**Before doing this**, test it by writing down the UUID for your root partition (/dev/sda3), then boot, hit ESC to get into grub menu, press 'e' to edit the first kernel entry, and replace /dev/sda3 with UUID=xxxxxxxxxx (where x's are the UUID you wrote down).

---

### Post by wwoollff on 2007-05-08
I've tried with the UUID at boot, but it didn't work.
/boot/grub/menu.lst - had already the UUID.Shall I change the kopt_2_6 too?
```

# kopt=root=UUID=8128ee1b-2a29-4a8a-a68a-45107f35067d ro
# kopt_2_6=root=/dev/sda3 ro

```
/boot/grub/devices.map
```

(hd0)   /dev/hda
(hd1)   /dev/sda

```

and thanks for having so much patience with me:)

---

### Post by mlind on 2007-05-08
Second kopt entry is only useful if you're booting into a kernel which has different root (/) filesystem. For instance, I have dual boot to Feisty and Edgy using kopt like this
```

# kopt=root=/dev/mapper/Ubuntu-root ro
# kopt_2_6_17=root=/dev/mapper/Ubuntu-rootEdgy ro

```
So if you don't have this kinda setup, remove the latter kopt entry (or put another # in the beginning so it's commented out). Then invoke "sudo update-grub" once again and try booting with a feisty kernel.

---

### Post by wwoollff on 2007-05-10
thx. problem solved. My fdisk -l changed and instead of sda3, it had sdb3 .I changed the menu.lst and now everything it's ok.Thk alot for your help.

---

