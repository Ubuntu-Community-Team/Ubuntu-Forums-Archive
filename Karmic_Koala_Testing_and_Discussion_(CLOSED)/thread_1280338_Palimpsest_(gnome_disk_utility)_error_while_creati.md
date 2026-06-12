---
title: "Palimpsest (gnome disk utility): error while creating filesystems"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gyruss on 2009-10-01
I have two systems that I've been gradually updating with dist-upgrade ever since Intrepid. I've been trying to use gnome disk utility to create a partition and filesystem and every time I get:

Error creating partition
The operation failed.
Error creating file system: helper exited with exit code 1: cannot create directory /var/run/DeviceKit-disks/job-mkfs-hE4dtX: No such file or directory

It looks like /var/run/DeviceKit-disks is never created during boot.

The disk getting the partition is a 300 GB SATA disk, nothing special.

---

