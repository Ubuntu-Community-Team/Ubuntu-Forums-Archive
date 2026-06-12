---
title: "LVM: One or more devices used as PVs in VG have changed sizes"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by livio on 2018-09-04
Hi guys, I recently installed LVM on Ubuntu 18.04 and I created my first LV. After first reboot I found a problem, as I cannot activate it anymore.
I noticed this error:

>     root@lvrome:/var/log# pvdisplay -v
        Wiping internal VG cache
        Wiping cache of LVM-capable devices
      WARNING: Device /dev/sdb has size of 312573551 sectors which is smaller than corresponding PV size of 312581808 sectors. Was device resized?
      One or more devices used as PVs in VG backup_vg have changed sizes.
      --- Physical volume ---
      PV Name               /dev/sdb
      VG Name               backup_vg
      PV Size               149,05 GiB / not usable <3,84 MiB
      Allocatable           yes (but full)
      PE Size               4,00 MiB
      Total PE              38156
      Free PE               0
      Allocated PE          38156
      PV UUID               LHDgmj-QGCd-xJnF-QhqH-B61a-iYnd-BpN2ZI
       
      --- Physical volume ---
      PV Name               /dev/sdd
      VG Name               backup_vg
      PV Size               149,05 GiB / not usable <3,84 MiB
      Allocatable           yes (but full)
      PE Size               4,00 MiB
      Total PE              38156
      Free PE               0
      Allocated PE          38156
      PV UUID               lXbczN-5bXe-C2lB-2Wq1-khbE-19SO-O3aHdI

Here there are some display commands for VG and PV:

>     root@lvrome:/media# vgdisplay 
      WARNING: Device /dev/sdb has size of 312573551 sectors which is smaller than corresponding PV size of 312581808 sectors. Was device resized?
      One or more devices used as PVs in VG backup_vg have changed sizes.
      --- Volume group ---
      VG Name               backup_vg
      System ID             
      Format                lvm2
      Metadata Areas        2
      Metadata Sequence No  4
      VG Access             read/write
      VG Status             resizable
      MAX LV                0
      Cur LV                1
      Open LV               0
      Max PV                0
      Cur PV                2
      Act PV                2
      VG Size               298,09 GiB
      PE Size               4,00 MiB
      Total PE              76312
      Alloc PE / Size       76312 / 298,09 GiB
      Free  PE / Size       0 / 0   
      VG UUID               lDCvsV-fOvb-qFWM-hjqF-9xbo-TClo-e0Vzca
    
    root@lvrome:/var/log# lvdisplay 
      WARNING: Device /dev/sdb has size of 312573551 sectors which is smaller than corresponding PV size of 312581808 sectors. Was device resized?
      One or more devices used as PVs in VG backup_vg have changed sizes.
      --- Logical volume ---
      LV Path                /dev/backup_vg/backup
      LV Name                backup
      VG Name                backup_vg
      LV UUID                lu8Jqs-7AD3-KNTH-2NP2-MQfP-zoxr-Ax2rPF
      LV Write Access        read/write
      LV Creation host, time lvrome, 2018-08-29 20:34:43 +0200
      LV Status              suspended
      # open                 0
      LV Size                298,09 GiB
      Current LE             76312
      Segments               1
      Allocation             inherit
      Read ahead sectors     auto
      - currently set to     256
      Block device           253:0

I tried to force activation for VG and then for LV, but I cannot go on:

>     root@lvrome:/media# vgchange -ay
      WARNING: Device /dev/sdb has size of 312573551 sectors which is smaller than corresponding PV size of 312581808 sectors. Was device resized?
      One or more devices used as PVs in VG backup_vg have changed sizes.
      device-mapper: resume ioctl on  (253:0) failed: Argomento non valido
      Unable to resume backup_vg-backup (253:0)
      1 logical volume(s) in volume group "backup_vg" now active
    root@lvrome:/media# lvchange -ay backup_vg
      WARNING: Device /dev/sdb has size of 312573551 sectors which is smaller than corresponding PV size of 312581808 sectors. Was device resized?
      One or more devices used as PVs in VG backup_vg have changed sizes.
      device-mapper: resume ioctl on  (253:0) failed: Argomento non valido
      Unable to resume backup_vg-backup (253:0)

I'm sure I haven't resized PVs after installation. By the way, I created them through `pvcreate /dev/sdb /dev/sdd`, `vgcreate backup_vg /dev/sdb /dev/sdd`, `lvcreate --type striped -i 2 -l 100%FREE -n backup backup_vg`.

That's my LVM version:

>     root@lvrome:/var/log# lvm version
      LVM version:     2.02.176(2) (2017-11-03)
      Library version: 1.02.145 (2017-11-03)
      Driver version:  4.37.0
      Configuration:   ./configure --build=x86_64-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --disable-silent-rules --libdir=${prefix}/lib/x86_64-linux-gnu --libexecdir=${prefix}/lib/x86_64-linux-gnu --runstatedir=/run --disable-maintainer-mode --disable-dependency-tracking --exec-prefix= --bindir=/bin --libdir=/lib/x86_64-linux-gnu --sbindir=/sbin --with-usrlibdir=/usr/lib/x86_64-linux-gnu --with-optimisation=-O2 --with-cache=internal --with-clvmd=corosync --with-cluster=internal --with-device-uid=0 --with-device-gid=6 --with-device-mode=0660 --with-default-pid-dir=/run --with-default-run-dir=/run/lvm --with-default-locking-dir=/run/lock/lvm --with-thin=internal --with-thin-check=/usr/sbin/thin_check --with-thin-dump=/usr/sbin/thin_dump --with-thin-repair=/usr/sbin/thin_repair --enable-applib --enable-blkid_wiping --enable-cmdlib --enable-cmirrord --enable-dmeventd --enable-dbus-service --enable-lvmetad --enable-lvmlockd-dlm --enable-lvmlockd-sanlock --enable-lvmpolld --enable-notify-dbus --enable-pkgconfig --enable-readline --enable-udev_rules --enable-udev_sync


Can you help me to find a solution?

---

