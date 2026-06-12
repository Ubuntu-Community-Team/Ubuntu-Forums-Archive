---
title: "Remount LVM after install to 7.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by brago on 2007-12-27
Hi,
Before I had a 7.04 installation with LVM configured and working well. I then tried to comand line upgrade to 7.10, but that was obviously beond my level of knowled because something failed and the system never worked very well. Today I did a clean install of 7.10, and now need some help to get my LVM to work again.

Before I did the reinstallation the LVM looked like this:
```
stefan@server:/var$ sudo pvdisplay
[sudo] password for stefan:
  Aborting - please provide new pathname for what used to be /dev/dm-6
  --- Physical volume ---
  PV Name               /dev/mapper/hda3
  VG Name               storage
  PV Size               132,92 GB / not usable 1,38 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              34026
  Free PE               0
  Allocated PE          34026
  PV UUID               kUDOs0-pYVQ-18uq-VnNl-MvxR-qrMM-q1KVV1

  --- Physical volume ---
  PV Name               /dev/mapper/hdb1
  VG Name               storage
  PV Size               74,53 GB / not usable 3,05 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              19079
  Free PE               0
  Allocated PE          19079
  PV UUID               RJuEFk-31v7-oZex-c0MQ-rLaW-SKbE-WjdTLR

  --- Physical volume ---
  PV Name               /dev/mapper/hde1
  VG Name               storage
  PV Size               279,46 GB / not usable 1,63 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              71541
  Free PE               134
  Allocated PE          71407
  PV UUID               GU18cj-NYVj-Me2N-UBPa-7LP0-nHtB-zvJlMe

stefan@server:/var$ sudo vgdisplay
  --- Volume group ---
  VG Name               storage
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               486,90 GB
  PE Size               4,00 MB
  Total PE              124646
  Alloc PE / Size       124512 / 486,38 GB
  Free  PE / Size       134 / 536,00 MB
  VG UUID               UoTK0M-NuHG-1U9O-toas-67HG-6YlO-09PJ31

stefan@server:/var$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/storage/Storage
  VG Name                storage
  LV UUID                m6eCpe-8j3i-eJxW-o4CV-DoXX-433O-7JT6jJ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                486,38 GB
  Current LE             124512
  Segments               3
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:5

stefan@server:/var$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              14G  4,8G  8,3G  37% /
varrun                379M  3,5M  376M   1% /var/run
varlock               379M  4,0K  379M   1% /var/lock
udev                  379M   31M  349M   9% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   35M  345M  10% /lib/modules/2.6.22-14-386/volatile
/dev/mapper/storage-Storage
                      479G  297G  163G  65% /storage
stefan@server:/var$
```

The I did the clean install, followed by installaing LVM2. Now the same command gives me the following infomration:

```
stefan@ubuntu-server:~$ sudo pvdisplay
[sudo] password for stefan:
  --- Physical volume ---
  PV Name               /dev/hda3
  VG Name               storage
  PV Size               132,92 GB / not usable 1,38 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              34026
  Free PE               0
  Allocated PE          34026
  PV UUID               kUDOs0-pYVQ-18uq-VnNl-MvxR-qrMM-q1KVV1

  --- Physical volume ---
  PV Name               /dev/hdb1
  VG Name               storage
  PV Size               74,53 GB / not usable 3,05 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              19079
  Free PE               0
  Allocated PE          19079
  PV UUID               RJuEFk-31v7-oZex-c0MQ-rLaW-SKbE-WjdTLR

  --- Physical volume ---
  PV Name               /dev/hde1
  VG Name               storage
  PV Size               279,46 GB / not usable 1,63 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              71541
  Free PE               134
  Allocated PE          71407
  PV UUID               GU18cj-NYVj-Me2N-UBPa-7LP0-nHtB-zvJlMe

stefan@ubuntu-server:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               storage
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               486,90 GB
  PE Size               4,00 MB
  Total PE              124646
  Alloc PE / Size       124512 / 486,38 GB
  Free  PE / Size       134 / 536,00 MB
  VG UUID               UoTK0M-NuHG-1U9O-toas-67HG-6YlO-09PJ31

stefan@ubuntu-server:~$ sudo lvdisplay
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver
  --- Logical volume ---
  LV Name                /dev/storage/Storage
  VG Name                storage
  LV UUID                m6eCpe-8j3i-eJxW-o4CV-DoXX-433O-7JT6jJ
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                486,38 GB
  Current LE             124512
  Segments               3
  Allocation             inherit
  Read ahead sectors     0

stefan@ubuntu-server:~$
```

I tried to mount the volume group by:

```
stefan@ubuntu-server:~$ cd /
stefan@ubuntu-server:/$ sudo mkdir storage
stefan@ubuntu-server:/$ sudo mount /dev/storage/Storage /storage
mount: special device /dev/storage/Storage does not exist
```

But that did not work quite as expected. Can anyone help me to get things right? I'm a bit afraid doing major misstakes which would make the information on the VG go away...

Thanks
Stefan

---

### Post by brago on 2007-12-27
I tried another command "sudo vgdisplay -v" to try and fix some issues and this is what I got:

```
stefan@ubuntu-server:/$ sudo vgdisplay -v
[sudo] password for stefan:
    Finding all volume groups
    Finding volume group "storage"
    Fixing up missing format1 size (132,92 GB) for PV /dev/hda3
    Fixing up missing format1 size (74,53 GB) for PV /dev/hdb1
    Fixing up missing format1 size (279,46 GB) for PV /dev/hde1
    Fixing up missing format1 size (132,92 GB) for PV /dev/hda3
    Fixing up missing format1 size (74,53 GB) for PV /dev/hdb1
    Fixing up missing format1 size (279,46 GB) for PV /dev/hde1
    Fixing up missing format1 size (132,92 GB) for PV /dev/hda3
    Fixing up missing format1 size (74,53 GB) for PV /dev/hdb1
    Fixing up missing format1 size (279,46 GB) for PV /dev/hde1
  --- Volume group ---
  VG Name               storage
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               486,90 GB
  PE Size               4,00 MB
  Total PE              124646
  Alloc PE / Size       124512 / 486,38 GB
  Free  PE / Size       134 / 536,00 MB
  VG UUID               UoTK0M-NuHG-1U9O-toas-67HG-6YlO-09PJ31

  --- Logical volume ---
  LV Name                /dev/storage/Storage
  VG Name                storage
  LV UUID                m6eCpe-8j3i-eJxW-o4CV-DoXX-433O-7JT6jJ
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                486,38 GB
  Current LE             124512
  Segments               3
  Allocation             inherit
  Read ahead sectors     0

  --- Physical volumes ---
  PV Name               /dev/hda3
  PV UUID               kUDOs0-pYVQ-18uq-VnNl-MvxR-qrMM-q1KVV1
  PV Status             allocatable
  Total PE / Free PE    34026 / 0

  PV Name               /dev/hdb1
  PV UUID               RJuEFk-31v7-oZex-c0MQ-rLaW-SKbE-WjdTLR
  PV Status             allocatable
  Total PE / Free PE    19079 / 0

  PV Name               /dev/hde1
  PV UUID               GU18cj-NYVj-Me2N-UBPa-7LP0-nHtB-zvJlMe
  PV Status             allocatable
  Total PE / Free PE    71541 / 134
```

And vgdisplay now shows:

```
stefan@ubuntu-server:/storage$ sudo vgdisplay
  --- Volume group ---
  VG Name               storage
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               486,90 GB
  PE Size               4,00 MB
  Total PE              124646
  Alloc PE / Size       124512 / 486,38 GB
  Free  PE / Size       134 / 536,00 MB
  VG UUID               UoTK0M-NuHG-1U9O-toas-67HG-6YlO-09PJ31
```

and finaly "sudo lvdisplay"


```
stefan@ubuntu-server:/storage$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/storage/Storage
  VG Name                storage
  LV UUID                m6eCpe-8j3i-eJxW-o4CV-DoXX-433O-7JT6jJ
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                486,38 GB
  Current LE             124512
  Segments               3
  Allocation             inherit
  Read ahead sectors     0

stefan@ubuntu-server:/storage$
```

Allways nice to get less error codes...

Anyhow, the webmin interface now shows me the logical volume. But when trying to mount it at /storage, I get a message that:

```
Failed to save mount : The device file '/dev/storage/Storage' does not exist
```

(*,)
/Stefan]

---

