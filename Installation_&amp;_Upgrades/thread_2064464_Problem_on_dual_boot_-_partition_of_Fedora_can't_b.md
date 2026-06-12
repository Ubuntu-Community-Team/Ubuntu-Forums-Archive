---
title: "Problem on dual boot - partition of Fedora can't be found on Ubuntu Home?"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-09-29
Fedora 17 64bit desktop
Ubuntu 12.04 64bit desktop

Ubuntu was installed first taking up the whole HD.  Then I installed Fedora by resizing Ubuntu partition making room for its installation.  Now I can boot either Fedora or Ubuntu

On Ubuntu terminal:-
$ sudo fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   153602047    76800000   83  Linux
/dev/sda2       296333310   312580095     8123393    5  Extended
/dev/sda3       153602048   154626047      512000   83  Linux
/dev/sda4       154626048   296331263    70852608   8e  Linux LVM
/dev/sda5       296333312   312580095     8123392   82  Linux swap / Solaris

Partition table entries are not in disk order

```

The partition of Fedora can't be found.

Neither it can be found on Ubuntu Home
see attached image file:
Screenshot_Ubuntu_Home.png

Under Devices
524MB is boot
see attached image file:
Screenshot_boot_partition.png


Fedora 17 terminal:
$ sudo fdisk -l
[sudo] password for satimis: ```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   153602047    76800000   83  Linux
/dev/sda2       296333310   312580095     8123393    5  Extended
/dev/sda3       153602048   154626047      512000   83  Linux
/dev/sda4       154626048   296331263    70852608   8e  Linux LVM
/dev/sda5       296333312   312580095     8123392   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/vg-lv_swap: 10.3 GB, 10267656192 bytes
255 heads, 63 sectors/track, 1248 cylinders, total 20054016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vg-lv_root: 41.5 GB, 41540386816 bytes
255 heads, 63 sectors/track, 5050 cylinders, total 81133568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vg-lv_home: 20.7 GB, 20736638976 bytes
255 heads, 63 sectors/track, 2521 cylinders, total 40501248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Ubuntu Home can be found on Fedora Home
see attached Screenshot_f17_home.png
under Devices
79 GB V,,,

Please advise how to detect Fedora partiton on running Ubuntu?

TIA

B.R.
satimis

---

### Post by darkod on 2012-09-29
As you can see in the fdisk results, Fedora installs as LVM.

Ubuntu doesn't include LVM by default unless is installed on LVM too. You can try adding the package and activating the LVM and then it should be detected.

```
sudo apt-get install lvm2
sudo vgchange -ay
```

See if that helps.

Since you planned to dual boot with Fedora and let it install as LVM you could have installed both OSs as LVM. It would have given you a bit more of flexibility too.

---

### Post by satimis on 2012-09-29
> **darkod said:**
> As you can see in the fdisk results, Fedora installs as LVM.

Ubuntu doesn't include LVM by default unless is installed on LVM too. You can try adding the package and activating the LVM and then it should be detected.

```
sudo apt-get install lvm2
sudo vgchange -ay
```

See if that helps.

Since you planned to dual boot with Fedora and let it install as LVM you could have installed both OSs as LVM. It would have given you a bit more of flexibility too.

Thanks for your advice.

$ sudo apt-get install lvm2
$ sudo vgchange -ay```

  3 logical volume(s) in volume group "vg" now active

```

$ sudo fdisk -l```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   153602047    76800000   83  Linux
/dev/sda2       296333310   312580095     8123393    5  Extended
/dev/sda3       153602048   154626047      512000   83  Linux
/dev/sda4       154626048   296331263    70852608   8e  Linux LVM
/dev/sda5       296333312   312580095     8123392   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/vg-lv_swap: 10.3 GB, 10267656192 bytes
255 heads, 63 sectors/track, 1248 cylinders, total 20054016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/vg-lv_home: 20.7 GB, 20736638976 bytes
255 heads, 63 sectors/track, 2521 cylinders, total 40501248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lv_home doesn't contain a valid partition table

Disk /dev/mapper/vg-lv_root: 41.5 GB, 41540386816 bytes
255 heads, 63 sectors/track, 5050 cylinders, total 81133568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lv_root doesn't contain a valid partition table

```

On Fedora Home I can't find user there.  It is empty
Pls see image file attached;
Screenshot_ubuntu_home_01.png

---

### Post by darkod on 2012-09-29
It's separate LV that's why. Notice how it said 3 logical volumes now active, not only 2.

And in the fdisk results notice lv_swap, lv_home and lv_root.

The users Home folders are in the 21GB filesystem (that's the lv_home logical volume of 21GB).

---

### Post by satimis on 2012-09-29
> **darkod said:**
> It's separate LV that's why. Notice how it said 3 logical volumes now active, not only 2.

And in the fdisk results notice lv_swap, lv_home and lv_root.

The users Home folders are in the 21GB filesystem (that's the lv_home logical volume of 21GB).
I see.  Thanks

satimis

---

