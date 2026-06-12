---
title: "NTFS and FAT32 partitions won't mount at boot."
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Rock on 2008-06-09
Ok, on my AMD Athlon 64 X2 5200+ 2.7GHz running Kubuntu 8.04, I can't seem to get these partitions to mount on boot and I did add them to my fstab.

This is my fstab.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=79fa133b-3498-43bd-863c-9b0ea4ad583d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
/dev/sdc5  /stuff defaults,user,dmask=027,fmask=137 0 0
# /dev/sda3
UUID=02652175-e41b-4a22-8071-915d9e1e672d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc6      /hdmovies   ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb1      /windows    ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by Habbit on 2008-06-09
You say they don't automount at boot - can you still mount them through the command line? If not, what is the output of the mount command? Anyways, what is the mount error at boot?

Have you checked the device names? Try to use UUIDs instead, they are available even for FAT and NTFS volumes (though they're shorter).

Is "ntfs-3g" still the correct fstype id in Hardy? My /etc/fstab has "ntfs" even though I know it uses ntfs-3g.

---

### Post by Rock on 2008-06-09
Yeah, I can mount them with the command line but it's really annoying to be forced to do that at boot. How do I use UUIDS? Yes, I think it is the correct type.

---

### Post by Habbit on 2008-06-09
Using UUIDs: you can get a filesystem UUID invoking vol_id -u blockdev, where blockdev is your partition (i.e. /dev/sdc6). Then, substitute that blockdev on fstab for UUID= and the uuid you obtained, just like the first entries.

In order to see what the boot mount error is, you might want to boot the system without the "splash" flag (and even without "quiet" too). You can do so from the GRUB menu.

Given that they are ntfs partitions, can you auto-mount them ("mount -a")? If not, can you mount them right away one by one (i.e. "mount /dev/sdc6") or do you need to use any flag ("mount -o force /dev/sdc6")? If you needed any flag, add them to fstab, to the "options" field.

---

### Post by Rock on 2008-06-09
> **Habbit said:**
> Using UUIDs: you can get a filesystem UUID invoking vol_id -u blockdev, where blockdev is your partition (i.e. /dev/sdc6). Then, substitute that blockdev on fstab for UUID= and the uuid you obtained, just like the first entries.

In order to see what the boot mount error is, you might want to boot the system without the "splash" flag (and even without "quiet" too). You can do so from the GRUB menu.

Given that they are ntfs partitions, can you auto-mount them ("mount -a")? If not, can you mount them right away one by one (i.e. "mount /dev/sdc6") or do you need to use any flag ("mount -o force /dev/sdc6")? If you needed any flag, add them to fstab, to the "options" field.
I don't have any errors, I don't think it's set to mount at the start up and when I do mount, I do it one by one using " mount /dev/sdb1 /windows" and such.

---

### Post by logos34 on 2008-06-09
this line (fat32 partition?)

> **Rock said:**
> 
# /dev/sdc5
/dev/sdc5 /stuff defaults,user,dmask=027,fmask=137 0 0

should be

> # /dev/sdc5
/dev/sdc5 /stuff [COLOR="Red"]vfat[/COLOR] defaults,user,dmask=027,fmask=137 0 0

Like Habbit says, use the uuids instead.  Find with:
[B]
ls -l /dev/disk/by-uuid[/B]

or
[B]
sudo vol_id /dev/sdb1[/B]

Or

** sudo blkid**

---

### Post by Rock on 2008-06-10
Problem is solved now because of using UUIDs with the sudo blkid command and this is my new working fstab.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=79fa133b-3498-43bd-863c-9b0ea4ad583d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID="442B-F31F" /stuff vfat defaults,umask=007,gid=46         0       0
# /dev/sda3
UUID=02652175-e41b-4a22-8071-915d9e1e672d none            swap    sw              0       0
# Removable Devices
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb6
UUID="882814F02814DECE" /hdmovies  ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sda1
UUID="10E82325E8230894" /windows    ntfs-3g defaults,locale=en_US.utf8 0 0



---

### Post by logos34 on 2008-06-10
> **Rock said:**
> Problem is solved now because of using UUIDs with the sudo blkid command and this is my new working fstab.

hmm...I see you copied the UUIDs with the " " ...Interesting, I thought you had to take those out for it to work (like your / and swap)

---

