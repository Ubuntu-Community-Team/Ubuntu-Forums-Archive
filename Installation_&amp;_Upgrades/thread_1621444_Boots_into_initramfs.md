---
title: "Boots into initramfs"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Hegh on 2010-11-14
After a rather convoluted upgrade (10.04 to 10.10)/downgrade (by updating sources.list and installing package versions from 10.04)/reinstallation (using the Kubuntu 10.04 alternate CD, because the package thing didn't work) process, my laptop is no longer able to complete the boot process, and drops me at an initramfs prompt.

The problem seems to be related to my LVM setup; it has trouble figuring out how to mount the root volume.

My current workaround is to add "break=premount" to the kernel command line (which also drops me at the initramfs prompt, but allows me to fix the problem and continue booting). At the prompt, I execute

```

# lvm vgscan
# lvm vgchange -a y
# mount -t ext4 /dev/primary_vg/root_lv /root
# exit

```

to complete the boot process.

I've tried re-installing the kernel, regenerating the initramfs (using 'update-initramfs -u'), re-applying Grub (using 'update-grub'), and even adding those lvm commands to the initramfs scripts in a couple of places.

I have a snapshot volume of my root partition from when I decided I didn't like 10.10 and would downgrade to 10.04. Unfortunately, I did not think to take a snapshot before upgrading to 10.10. If necessary, I should be able to go back to 10.10 (which had no problems booting), but I would rather fix 10.04.

Does anyone have any suggestions? Even if it's just a hack, I don't want to be manually involved with the boot process.

Here is some diagnostic information:

fdisk -l:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa350a350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1543       22262   166426968    7  HPFS/NTFS
/dev/sda4           22263       38913   133747713    5  Extended
/dev/sda5           22263       22384      974848   83  Linux
/dev/sda6           22384       23113     5858304   82  Linux swap / Solaris
/dev/sda7           23114       30762    61440000   8e  Linux LVM
/dev/sda8           30763       38913    65471488   8e  Linux LVM

```

fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/primary_vg-root_lv /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=b04eca33-e367-42ad-8d6c-7303d1c435fe /boot           ext4    defaults        0       2
/dev/mapper/primary_vg-home_lv /home           ext4    defaults        0       2
# /windows/boot was on /dev/sda2 during installation
UUID=E87244C772449C66 /windows/boot   ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows/c was on /dev/sda3 during installation
UUID=5E144BE2144BBBB1 /windows/c      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows/recovery was on /dev/sda1 during installation
UUID=DAA41C49A41C2B11 /windows/recovery ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=b87fd0d7-4b73-4c69-9a0c-f9bdc5ada645 none            swap    sw              0       0

```

pvdisplay:
```

  --- Physical volume ---
  PV Name               /dev/sda7
  VG Name               primary_vg
  PV Size               58.59 GiB / not usable 3.81 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              14999
  Free PE               0
  Allocated PE          14999
  PV UUID               lMduRt-RRrE-IVUb-pSPu-aD2O-05Yo-6cKShc
   
  --- Physical volume ---
  PV Name               /dev/sda8
  VG Name               primary_vg
  PV Size               62.44 GiB / not usable 1.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              15984
  Free PE               4314
  Allocated PE          11670
  PV UUID               vr1K7g-0cWd-tkdU-SDdd-0dR7-XkFt-YykGl2

```

vgdisplay:
```

  --- Volume group ---
  VG Name               primary_vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  21
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               121.03 GiB
  PE Size               4.00 MiB
  Total PE              30983
  Alloc PE / Size       26669 / 104.18 GiB
  Free  PE / Size       4314 / 16.85 GiB
  VG UUID               UJ4uhU-6S4v-3Im4-303N-eHto-dDY6-0c3T1q

```

lvdisplay:
```

  --- Logical volume ---
  LV Name                /dev/primary_vg/root_lv
  VG Name                primary_vg
  LV UUID                tT0MiJ-ABnt-h0Nj-x8eX-sFEG-i9aY-8jVFnA
  LV Write Access        read/write
  LV snapshot status     source of
                         /dev/primary_vg/snap_root_lv [active]
  LV Status              available
  # open                 1
  LV Size                19.18 GiB
  Current LE             4909
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/primary_vg/home_lv
  VG Name                primary_vg
  LV UUID                I6S4iv-rpDl-hiLW-qef4-5TSy-pNxr-iHKJ4u
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                70.00 GiB
  Current LE             17920
  Segments               5
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Logical volume ---
  LV Name                /dev/primary_vg/snap_root_lv
  VG Name                primary_vg
  LV UUID                87adf1-ePsH-Zf5j-t7Ci-6YOY-TA9q-wUfCEZ
  LV Write Access        read/write
  LV snapshot status     active destination for /dev/primary_vg/root_lv
  LV Status              available
  # open                 0
  LV Size                19.18 GiB
  Current LE             4909
  COW-table size         15.00 GiB
  COW-table LE           3840
  Allocated to snapshot  53.42% 
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

```

---

### Post by Hegh on 2011-01-10
I deleted the root snapshot partition the other day, and suddenly the machine boots normally.

Perhaps I should file a bug...

---

### Post by blablagiggles on 2011-09-29
where can i find the root snapshot partition? ):P i have the same problem where i always need to type-in "exit" just to continue booting

---

### Post by Hegh on 2011-10-01
> **blablagiggles said:**
> where can i find the root snapshot partition? ):P i have the same problem where i always need to type-in "exit" just to continue booting

You would have had to create one. Mine is at the bottom of the lvdisplay output in my initial post. I created it as snap_root_lv, and it shows an "LV snapshot status" as "active destination for /dev/primary_vg/root_lv".

If you have a root snapshot volume, it will show up when you execute

```
sudo lvdisplay
```

If you find such a volume, you can get rid of it with

```
sudo lvremove /path/to/snapshot/volume
```

but BE CAREFUL, because if you get it wrong, you can lose an entire volume. You will need to unmount it first if it is mounted (unlikely with a snapshot volume).

---

### Post by blablagiggles on 2011-10-01
ah. i miss understood your posts, sorry. Anyway, i have a similar problem where i end up at busybox/initramfs. Curiously though, when i enter "exit" (without any previous command), ubuntu boots normally. any idea on this?

---

### Post by Hegh on 2011-10-02
> **blablagiggles said:**
> ah. i miss understood your posts, sorry. Anyway, i have a similar problem where i end up at busybox/initramfs. Curiously though, when i enter "exit" (without any previous command), ubuntu boots normally. any idea on this?

I don't know. My only suggestion would be to modify your initrd scripts and see if there is some kind of timeout that you could increase. You'll probably have better luck posting a new thread and asking for everybody's suggestions.

---

