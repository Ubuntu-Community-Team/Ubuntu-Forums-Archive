---
title: "fsck problems on boot"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by rabidityfactor on 2009-11-13
Hi..
I just upgraded to karmic from jaunty. But when i boot, after the first logo screen it drops to command screen saying something about fsck. Boot then resumes properly.
When I do an fsck, I get this error. How do I correct it?
```
rohith@messiah:~$ fsck
fsck from util-linux-ng 2.16
fsck.ext3: Unable to resolve 'UUID=a7f41202-9f03-4245-9b18-beffb1786577'

```
fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a7f41202-9f03-4245-9b18-beffb1786577 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=2cfa7638-f105-42f9-812d-9aa6cd435bf9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/alpha auto defaults 0 0
/dev/sda5 /media/beta auto defaults 0 0
```
```
fdisk -l
cannot open /proc/partitions
```
```
rohith@messiah:~$ cat /proc/partitions
cat: /proc/partitions: No such file or directory
```
Thanks

---

### Post by lemming465 on 2009-11-15
Does *ls /proc* show an empty directory, or something with about 200-300 entries including devices, cmdline, cpuinfo, kmsg, mdstat, meminfo, filesystems, etc?  Failure to mount /proc is pretty bizarre to me, unless the /proc directory is missing.

What does *sudo blkid* show?  If it complains, try running it from a live CD instead.

---

### Post by _mikec_ on 2009-11-16
i have the same problem, the boot time hangs for like 3 minutes on that message and this is a new installation of ubuntu karmic 9.10.
>  fsck from util-linux-ng...
 ......[sdc] assuming drive cache: write through how can i fix this problem, anyone found a solution ?  thanks

sudo blkid
> /dev/sda1: UUID="96DC7C4DDC7C2A1F" TYPE="ntfs" 
/dev/sda5: UUID="51df1e26-1c2d-40f6-9779-f7aa5233aefa" TYPE="ext4" 
/dev/sda6: UUID="ed17f3a6-6454-4710-a673-ad4171b8e5d7" TYPE="swap" 
/dev/sdb1: LABEL="CLM-^P USB" UUID="5824-0D2D" TYPE="vfat" 

---

### Post by lemming465 on 2009-11-16
Mike, could we see the output from *cat /etc/fstab*?

---

### Post by rabidityfactor on 2009-11-17
Well.. actually I solved the problem....

REINSTALLED..!! :D

---

### Post by _mikec_ on 2009-11-21
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=51df1e26-1c2d-40f6-9779-f7aa5233aefa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ed17f3a6-6454-4710-a673-ad4171b8e5d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

here goes my /etc/fstab

---

