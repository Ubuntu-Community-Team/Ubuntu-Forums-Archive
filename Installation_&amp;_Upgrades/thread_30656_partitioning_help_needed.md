---
title: "partitioning help needed"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by elebrin on 2005-04-29
I currently have Ubuntu installed and I need to reinstall filesystems on the partitions of a 200GB drive (they were vfat and I would like them to be ext3 so I can set permissions correctly).

I have tried using gparted, but after I build the FS, the partitions refuse to mount with the line:

/dev/hdb5        /mnt/location        ext3         defaults,user,uid=1000 0     0

(with the correct partition numbers, hdb5,6,7,8,9,1) and it refuses to mount.  When I remove the uid=1000 it mounts fine, but I don't want to have to chroot/sudo/su to access my data all the time.  Also, when I fdisk -l, it says that the partitions are still formatted with vfat (which they shouldn't be), so I have no idea what filesystem they actually are (gparted says they are ext3).

Are there any command-line tools I can use to do this correctly?  I simply want to install ext3 on these partitions and be done with it. I would be MORE then willing to RTFM if I knew which M to FR.

---

### Post by nad on 2005-04-29
Use the mount options: rw,user,noauto . They should now show up in Places -> Computer and on your desktop if gvm is working today. To mount them just double click.

To doublecheck your ext2/3 filesystems: e2fsck -v /dev/hdbx  where 'x' is the partition number and your filesystem is not mounted.

The manuals would be: man e2fsck, man mkfs.ext3, man tune2fs, man parted, etc or try the command line tool xman which is an archaic manual pager that takes a little getting used to.
It's like using a dictionary to find the spelling of a word. Knowing what you are looking for makes it easier to find. They really do need to make reading manual pages easier and more prominent.

---

