---
title: "vgchange  won' t activate partition- device-mapper: create ioctl is busy"
date: 2018-03-07
forum: Installation &amp; Upgrades
---

### Post by harterc2 on 2018-03-07
I recently installed 10.10.1.  I can't get it to boot right yet.  So I was trying to mount it chroot and try to fix the boot.
I can't mount it to chroot to it.  I use the ubuntu live disk.  The root partion partition is a mirrored lv in a luks container.
the error message that I get is:
 vgchange -a y --sysinit 
  WARNING: Device /dev/mapper/sdc5_crypt has size of 1952318144 sectors which is smaller than corresponding PV size of 1952518144 sectors. Was device resized?
  WARNING: Device /dev/mapper/kubuntu2_vg-root has size of 1952318144 sectors which is smaller than corresponding PV size of 3998355945472 sectors. Was device resized?
  One or more devices used as PVs in VG kubuntu2_vg have changed sizes.
  device-mapper: create ioctl on kubuntu2_vg-rootLVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQeanUsV2PrL0c7fhnwYyPdn1AXrk69Thf failed: Device or resource busy
  device-mapper: resume ioctl on (253:6) failed: Invalid argument
  Unable to resume kubuntu2_vg-swap_1 (253:6)
  1 logical volume(s) in volume group "kubuntu2_vg" now active

It just won't activate.  I have attached a debug file of the command.
Using a special rescue disk, I am able to activate it and mount it.  I just can't do that with the ubuntu live cd

---

### Post by QIII on 2018-03-07
Are you talking about Ubuntu 10.10, Maverick Meerkat?

---

### Post by harterc2 on 2018-03-08
> **QIII said:**
> Are you talking about Ubuntu 10.10, Maverick Meerkat?

It is the latest 17.10. That was a typo.

---

### Post by harterc2 on 2018-03-08
Here is some information from strace of vgchange -a y.
stat("/dev/mapper/sdc5_crypt", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 0), ...}) = 0
stat("/dev/mapper/sdc5_crypt", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 0), ...}) = 0
stat("/dev/mapper/sdc5_crypt", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 0), ...}) = 0
stat("/dev/mapper/sdc5_crypt", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 0), ...}) = 0
stat("/dev/mapper/kubuntu2_vg-root", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 1), ...}) = 0
stat("/dev/mapper/kubuntu2_vg-root", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 1), ...}) = 0
stat("/dev/mapper/kubuntu2_vg-root", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 1), ...}) = 0
stat("/dev/mapper/kubuntu2_vg-root", {st_mode=S_IFBLK|0660, st_rdev=makedev(253, 1), ...}) = 0
ioctl(5, DM_TABLE_STATUS, {version=4.0.0, data_size=16384, data_start=312, dev=makedev(253, 2), flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG} => {version=4.37.0, data_size=369, data_start=312, dev=makedev(253, 2), name="kubuntu2_vg-root_rmeta_0", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQE4r43uvles0DlY2hxyFftwCJ0bdltebt", target_count=1, open_count=0, event_nr=0, flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG|DM_ACTIVE_PRESENT_FLAG, ...}) = 0
ioctl(5, DM_TABLE_STATUS, {version=4.0.0, data_size=16384, data_start=312, dev=makedev(253, 3), flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG} => {version=4.37.0, data_size=363, data_start=312, dev=makedev(253, 3), name="kubuntu2_vg-root_rimage_0", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQB3WWlJEq70rDpQQHS96kyg4Qv3asSc90", target_count=1, open_count=0, event_nr=0, flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG|DM_ACTIVE_PRESENT_FLAG, ...}) = 0
ioctl(5, DM_TABLE_STATUS, {version=4.0.0, data_size=16384, data_start=312, dev=makedev(253, 4), flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG} => {version=4.37.0, data_size=363, data_start=312, dev=makedev(253, 4), name="kubuntu2_vg-root_rmeta_1", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQGq4pyWj3VkDhrWMXXZYE7awnti6DFE46", target_count=1, open_count=0, event_nr=0, flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG|DM_ACTIVE_PRESENT_FLAG, ...}) = 0
ioctl(5, DM_TABLE_STATUS, {version=4.0.0, data_size=16384, data_start=312, dev=makedev(253, 5), flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG} => {version=4.37.0, data_size=364, data_start=312, dev=makedev(253, 5), name="kubuntu2_vg-root_rimage_1", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQ96dhUh1apbW5yDhkV3u0DY1o0oJ4e6F7", target_count=1, open_count=0, event_nr=0, flags=DM_EXISTS_FLAG|DM_PERSISTENT_DEV_FLAG|DM_STATUS_TABLE_FLAG|DM_ACTIVE_PRESENT_FLAG, ...}) = 0
ioctl(5, DM_DEV_CREATE, {version=4.0.0, data_size=16384, name="kubuntu2_vg-root", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQeanUsV2PrL0c7fhnwYyPdn1AXrk69Thf", flags=DM_EXISTS_FLAG|DM_SKIP_BDGET_FLAG} => {version=4.37.0, data_size=16384, name="kubuntu2_vg-root", uuid="LVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQeanUsV2PrL0c7fhnwYyPdn1AXrk69Thf", flags=DM_EXISTS_FLAG|DM_SKIP_BDGET_FLAG}) = -1 EBUSY (Device or resource busy)
write(2, "  ", 2  )                       = 2
write(2, "device-mapper: create ioctl on k"..., 147device-mapper: create ioctl on kubuntu2_vg-rootLVM-YCm8GIDardvLgtz45dtOwWy8jvrwK3vQeanUsV2PrL0c7fhnwYyPdn1AXrk69Thf failed: Device or resource busy) = 147

---

### Post by harterc2 on 2018-03-08
Here is the output of udevmonitor when vgchange -a y --sysinit is run:
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[84065.960257] add      /devices/virtual/bdi/253:8 (bdi)
KERNEL[84065.960280] add      /devices/virtual/block/dm-8 (block)
UDEV  [84065.960847] add      /devices/virtual/bdi/253:8 (bdi)
KERNEL[84065.976076] remove   /devices/virtual/bdi/253:8 (bdi)
KERNEL[84065.976141] remove   /devices/virtual/block/dm-8 (block)
UDEV  [84065.976342] remove   /devices/virtual/bdi/253:8 (bdi)
UDEV  [84066.000242] add      /devices/virtual/block/dm-8 (block)
UDEV  [84066.000640] remove   /devices/virtual/block/dm-8 (block)

---

### Post by harterc2 on 2018-03-10
I eventually turned off the mirroring.  It would still complain about the other luks partition not being present.   I would then have to luksOpen that so it could see the luks blkid.
Later I created a new vg with the 2nd mirrored partition and was able to chroot it.
I have root luks partitions on my laptop that work with this same ubuntu distribution- artfull.
It seems that when it sees mirrored lvm partition that it can't handle it.  Or perhaps the config has to be just right and there is no flexibility on that.

---

### Post by harterc2 on 2018-03-10
Just when I thought I had this problem fixed. I can't mount the luks partition with the live disk again.
vgchange -a y -v --sysinit
    Activating logical volume vg1/root.
    activation/volume_list configuration setting not defined: Checking only host tags for vg1/root.
    Creating vg1-root
  device-mapper: create ioctl on vg1-rootLVM-dwtqIgPDHhWxYKGqaGIGAuIO7xWyLS80RA9l1tPqi12iuf0HsSmVUi0t0Qs03yOC failed: Device or resource busy
    Activated 0 logical volumes in volume group vg1
  0 logical volume(s) in volume group "vg1" now active

Here is output from when I run cryptsetup luksOpen:
udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1323.245407] add      /devices/virtual/bdi/253:0 (bdi)
KERNEL[1323.245428] add      /devices/virtual/block/dm-0 (block)
KERNEL[1323.245443] change   /devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc5 (block)
UDEV  [1323.245991] add      /devices/virtual/bdi/253:0 (bdi)
KERNEL[1323.246091] change   /devices/virtual/block/dm-0 (block)
UDEV  [1323.247565] change   /devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc5 (block)
UDEV  [1323.292278] add      /devices/virtual/block/dm-0 (block)
KERNEL[1323.321604] add      /devices/virtual/bdi/253:1 (bdi)
KERNEL[1323.321636] add      /devices/virtual/block/dm-1 (block)
UDEV  [1323.321920] add      /devices/virtual/bdi/253:1 (bdi)
KERNEL[1323.336086] remove   /devices/virtual/bdi/253:1 (bdi)
KERNEL[1323.336138] remove   /devices/virtual/block/dm-1 (block)
UDEV  [1323.336411] remove   /devices/virtual/bdi/253:1 (bdi)
UDEV  [1323.339432] change   /devices/virtual/block/dm-0 (block)
UDEV  [1323.340202] add      /devices/virtual/block/dm-1 (block)
UDEV  [1323.340513] remove   /devices/virtual/block/dm-1 (block)
When I run this command 
vgchange -a y --sysinit
  device-mapper: create ioctl on vg1-rootLVM-dwtqIgPDHhWxYKGqaGIGAuIO7xWyLS80RA9l1tPqi12iuf0HsSmVUi0t0Qs03yOC failed: Device or resource busy
  0 logical volume(s) in volume group "vg1" now active
I get this in the monitor window for udev:

KERNEL[1410.408672] add      /devices/virtual/bdi/253:1 (bdi)
KERNEL[1410.408693] add      /devices/virtual/block/dm-1 (block)
UDEV  [1410.409256] add      /devices/virtual/bdi/253:1 (bdi)
KERNEL[1410.424096] remove   /devices/virtual/bdi/253:1 (bdi)
KERNEL[1410.424132] remove   /devices/virtual/block/dm-1 (block)
UDEV  [1410.424384] remove   /devices/virtual/bdi/253:1 (bdi)
UDEV  [1410.444238] add      /devices/virtual/block/dm-1 (block)
UDEV  [1410.444591] remove   /devices/virtual/block/dm-1 (block)

Any ideas on what might be causing this?

---

### Post by harterc2 on 2018-03-10
I go it to mount again.  Perhaps it is in the name which is to similar to the vg.
Here is the command history:
cryptsetup luksClose /dev/vg1/root
   54  ls /dev/mapper
   55  cryptsetup luksClose vg1-root
   56  vgchange -a y vg1
   57  cryptsetup luksOpen /dev/sdc5 sdc5_crypt
   58  lvscan
   59  lvdisplay
   60  mount  /dev/vg1/root /mnt
Now to fix my boot problem.

---

