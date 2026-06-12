---
title: "e2fsck does not fix read-only filesystem"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hart02 on 2009-10-08
The title say a lot. I installed karmic since I had issues with jaunty and did not want to reinstall it with karmic coming. it went fine until something happened where it is now read only.

did this and 

```
sudo e2fsck -f -y -v /dev/sda1
```
 
nothing

then I edit /etc/fstab to look like this

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ea3e8d24-7e27-47f1-b0b0-ab8106d09554 /               ext4    errors=continue 0       1
# swap was on /dev/sda5 during installation
UUID=6085bdd8-5527-4112-839e-8f976e6aad8f none            swap    sw              0       0
/dev/sdb1 /media/9f1fa354-27bb-4dcc-86de-b563feaa0a92 ext3 rw,auto,nosuid,nodev,relatime,uhelper=devkit 0 0
/dev/sdc1 /media/693f73da-8952-4d7c-afd7-8b22ac67b5f0 ext3 rw,auto,nosuid,nodev,relatime,uhelper=devkit 0 0
/dev/sdd1 /media/290de143-05c4-4e32-a23e-e0db8af965a1 ext3 rw,auto,nosuid,nodev,relatime,uhelper=devkit 0 0
```

Still does it 

I am at a loss and I cant boot into recovery mode to do this

```
sudo mount -n -o remount,rw / 
```

Here is some debugging output
```
root@ubuntu:/# dmesg | tail
[  702.511428]  sdh: sdh1
[  702.513426] sd 7:0:0:0: [sdh] Assuming drive cache: write through
[  702.513429] sd 7:0:0:0: [sdh] Attached SCSI removable disk
[  759.343677] EXT4-fs (sda1): barriers enabled
[  759.358521] kjournald2 starting: pid 3880, dev sda1:8, commit interval 5 seconds
[  759.358711] EXT4-fs (sda1): internal journal on sda1:8
[  759.358714] EXT4-fs (sda1): delayed allocation enabled
[  759.358716] EXT4-fs: file extents enabled
[  759.390427] EXT4-fs: mballoc enabled
[  759.390438] EXT4-fs (sda1): mounted filesystem with ordered data mode
root@ubuntu:/# dmesg | tail /var/log/messages
Oct  5 12:45:40 bmanspc kernel: [   14.845025] Bridge firewalling registered
Oct  5 12:45:40 bmanspc kernel: [   20.364673] ppdev: user-space parallel port driver
Oct  5 12:45:40 bmanspc kernel: [  420.096880] at-spi-registry[1844]: segfault at 0 ip (null) sp bff2d31c error 4 in libXtst.so.6.1.0[110000+4000]
Oct  5 12:45:46 bmanspc kernel: [ 3667.000045] ata2: hard resetting link
Oct  5 12:45:46 bmanspc kernel: [ 3667.000046] ata2: nv: skipping hardreset on occupied port
Oct  5 12:45:46 bmanspc kernel: [ 3668.500048] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  5 12:45:46 bmanspc kernel: [ 3673.500023] ata2.00: qc timeout (cmd 0xec)
Oct  5 12:45:46 bmanspc kernel: [ 3673.500030] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Oct  5 12:45:46 bmanspc kernel: [ 3673.500043] ata2: hard resetting link
Oct  6 00:21:25 bmanspc kernel: Kernel logging (proc) stopped.
root@ubuntu:/# 

```:confused:
 I spent alot of time redoing my system and to redo it again would mean beating my head on the wall.help would be appreciated.

---

### Post by philinux on 2009-10-08
Report your post and ask the mods to move your thread to the karmic testing forum. You might get an answer there.

---

### Post by hart02 on 2009-10-08
Well any takers

---

### Post by VMC on 2009-10-08
You can use your livecd to chroot over to you system then try ```
sudo mount -n -o remount,rw /
```

---

### Post by hart02 on 2009-10-09
Ok it is fixed turns out that the runit package causes the freezing. i purged it and it boots fine.

---

