---
title: "Can't see hda &amp; hdb after failed upgrade attempt"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by dsiddens on 2007-10-23
The two hard disks in the HP dv8000 AMD64 laptop seem to have disappeared after a failed install attempt via Synaptic Package Manager "7.10 update available" method.  I have since been able to make a 7.10 boot CD using our other laptop.  Infact I'm posting this help call from the HP dv8000 AMD64 using Gutsy as a live CD.  This is progress!

Now I'm trying to get the system to recognize the previous hda & hdb.
When I look with Krusader root privileges, mountman, I see the following:
/dev/sda1, vfat; /dev/sda5,ext3 and unionfs, unionfs.  Their respective mount points are: /media/disk-1; /media/disk and /.

sdax is an  external hard drive.

Help, please, to get back the two drives inside this laptop.

Thank you, Doug

---

