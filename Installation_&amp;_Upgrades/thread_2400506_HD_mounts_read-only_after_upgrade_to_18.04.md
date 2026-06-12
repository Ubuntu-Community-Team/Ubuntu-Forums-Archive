---
title: "HD mounts read-only after upgrade to 18.04"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by chubbtech on 2018-09-06
My OS runs from an sdd and I have a 1TB hdd for my pictures-music....   Since the upgrade those folders are read-only here's my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e635346c-acb6-417b-a2a3-661764b5cd76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=18b96681-db58-4518-8438-4aafbf3b08ed none            swap    sw              0       0
/dev/disk/by-uuid/7c4b6cb9-68b1-489e-a1bf-c25c59e60052 /mnt/7c4b6cb9-68b1-489e-a1bf-c25c59e60052 auto nosuid,nodev,nofail,x-gvfs-show 0 0

that last line seems to be the problem but not sure how to fix it.  that uuid is the one for my hdd (checked with blkid)

thx

---

### Post by chubbtech on 2018-09-06
and here's the blkid output

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="e635346c-acb6-417b-a2a3-661764b5cd76" TYPE="ext4" PARTUUID="8e624cbd-01"
/dev/sda5: UUID="18b96681-db58-4518-8438-4aafbf3b08ed" TYPE="swap" PARTUUID="8e624cbd-05"
/dev/sdb1: UUID="7c4b6cb9-68b1-489e-a1bf-c25c59e60052" TYPE="ext4" PARTUUID="000c2644-01"
/dev/sdb5: UUID="c1118acf-9bde-4c78-a351-0070aeacb020" TYPE="swap" PARTUUID="000c2644-05"
/dev/sdc1: UUID="6137698D7CF176DC" TYPE="ntfs" PARTUUID="0003f448-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"

---

