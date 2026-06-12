---
title: "NTFS file system not in /etc/fstab"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2008-09-22
I just installed Hardy Heron on a PC with 2 hard drives.  Partition sda1 is a Windows XP NTFS partition and sdb1 is the Ubuntu ext3 partition.  The installation did not put an entry for the NTFS partition into /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f900070e-2701-4360-98c3-68bc817d012b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d8a7d02f-441c-4d94-8db3-df02963da66b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

The NTFS partition is apparently dynamically mounted on /media/disk-1 when I click on the icon for the partition under "Places" or if I follow a soft-link I defined from my home directory on Ubuntu over to my home directory on Windows, but any attempt to access a file in the NTFS partition before I do that manual operation fails, and for some reason applications under Wine cannot access files even after the file system is mounted.

My unix knowledge is rusty.  I worked in Solaris 10 years ago, but a lot of things have changed and support for NTFS is brand new.  How can I modify /etc/fstab to mount the NTFS partition at startup?

---

### Post by vanadium on 2008-09-22
You correctly described the new behaviour in Hardy. You also correctly indicate that you still can mount an ntfs volume in /etc/fstab. You do this the usual way as with other volumes. As file system type, specify "ntfs-3g" for read/write support, or "ntfs" to use the traditional (read-only) ntfs driver.

To find the correct UUID for your volume, use "sudo blkid". Using UUIDs to refer to a partition is nowadays preferred over using device names.

---

