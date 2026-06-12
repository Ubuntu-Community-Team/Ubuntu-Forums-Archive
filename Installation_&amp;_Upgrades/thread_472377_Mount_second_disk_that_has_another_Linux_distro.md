---
title: "Mount second disk that has another Linux distro"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by h20Boodle on 2007-06-13
I'm trying to recover files from an old disk drive I have that has Fedora Core 4 (FC4) on it.  When I tried mounting it, I don't see the filesystems as I'd expect, but instead I only see the image files. Will someone please tell me how I can mount the disk so I can see the directories and files as normal? I don't have problems mounting disks that have never had an OS installed on them, but since this drive was once my main drive, I  can't figure out how to mount it so I can retrieve the files to my new drive that has Ubuntu on it.

-- Edit --

I learned that Fedora Core 4 was using LVM (Logical Volume Manager?), so I had to load up a few tools to allow me to mount the volume that held the /home directory.

sudo modprobe dm-mod  # Not sure if this was necessary
vgchange -ay # Found "vgchange" in the lvm2 package
sudo mount /dev/VolGroup00/LogVol00 /mnt/disk3 # mounted the volume

---

