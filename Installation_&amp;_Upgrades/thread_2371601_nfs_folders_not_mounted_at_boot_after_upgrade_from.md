---
title: "nfs folders not mounted at boot after upgrade from 16.04 to 17.04"
date: 2017-09-16
forum: Installation &amp; Upgrades
---

### Post by bnebenda on 2017-09-16
I recently upgraded from 16.04 LTS to 17.04. Previously I had a couple of folders mounted from a Synology Disk Station using the following fstab file (last 5 entries):

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=691ee3a4-ee35-4e56-8445-10f0b681eed4 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
diskstation.fritz.box:/volume1/document /nfs/diskstation/document nfs rw,hard,intr 0 2
diskstation.fritz.box:/volume1/music /nfs/diskstation/music nfs rw,hard,intr 0 2
diskstation.fritz.box:/volume1/photo /nfs/diskstation/photo nfs rw,hard,intr 0 2
diskstation.fritz.box:/volume1/video /nfs/diskstation/video nfs rw,hard,intr 0 2
diskstation.fritz.box:/volume1/tv-recording /nfs/diskstation/tv-recording nfs rw,hard,intr 0 2

```

Manually mounting them using 

sudo mount -a

works as expected, but they are not mounted at boot time anymore. Any idea how to fix that?

Bernd

---

### Post by bnebenda on 2017-09-16
Hello,

when switching from 16.04 to 17.04 initially I had some issues with networking so I temparily switched from wireline to wifi networking. That is when the mount problem showed up. Just a few minutes ago was able to figure out how to get the wired networking back again. This magically solved my mount issue. 

Any explanation?

Bernd

---

