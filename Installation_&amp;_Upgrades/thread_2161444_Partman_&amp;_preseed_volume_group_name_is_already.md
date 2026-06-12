---
title: "Partman &amp; preseed: volume group name is already in use"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by CyberAngel on 2013-07-10
I have the following disk setup:

> sda1 -> /boot
sda5 (physical volume) -> vg0 (volume group)
vg0 -> root-lvm, swap-lvm, storage-lvm (logical volumes)
storage-lvm (physical volume) -> myapp-volume-group (volume group)

To explain a little bit better: sda is the real hard disk which is split in two partitions. sda1 and sda5.
sda1 is ext2 and contains /boot and sda5 is initialized as a physical volume for the default volume group vg0.
On vg0 I have three logical volumes. The root (/), swap and one that I call it storage.

Now here is the tricky part. Because one application I run needs to manage a whole volume group with a given name (myapp-volume-group), I create a "physical volume" (pvcreate) on storage-lvm logical volume, and on top of that I create the "myapp-volume-group".

This works fine for the app but the problem comes when I try to reinstall this machine using a preseed file which fails with this error: "volume group name is already in use".

When I try to remove the vg0 manually from the command line (alt+f2 during the setup) I get the following error:

```
~ # vgremove vg0
Do you really want to remove volume group "vg0" containing 1 logical volumes? [y/n]: y
  Can't remove open logical volume "storage"
```

If I remove manually the lvm's under the "myapp-volume-group", then the above works fine.

Is there any way to force the removal of vg0 even when the "storage" logical volume is open?
How can I get past a situation like this with a preseed file?

---

