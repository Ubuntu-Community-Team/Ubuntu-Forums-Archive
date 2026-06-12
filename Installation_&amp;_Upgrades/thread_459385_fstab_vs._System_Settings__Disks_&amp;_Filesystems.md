---
title: "fstab vs. System Settings : Disks &amp; Filesystems"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Rambo Tribble on 2007-05-30
I upgraded to the latest Feisty kernel on a Kubuntu install and am getting some strange results vis-a-vis what is in fstab and what is appearing in the System Settings: Disk & Filesystems dialog. 

First, the fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=03f87475-b108-4030-abb8-00f89a8f0c18 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda6
UUID=36fceef5-031d-4461-8b8a-6afddb7a74ff /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=8AEC4819EC480245 /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda7
UUID=e4809327-19ad-42de-b1d3-106aee55f54d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda8 /media/sda8 auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

Now the disk has as its first primary partition a ntfs partition. The second partition is an extended one and logical partition 5 is root and 6 is home, with 7 as swap and 8 has a second Linux installation (a Dapper variant). 

System Settings: Disk & Filesystems reports the results of this arrangement differently with the 2.6.20-15 kernel than with 2.6.20-16, but neither would seem correct. In either the sda1 partition reports as expected; in -15 Partition 2 is listed as /dev/fd0 with a mount of /media/floppy0 and is disabled. The other partitions then are reported as one would expect. 

In -16 it is similar for Partition 1, though the device is listed as /dev/hda1, instead of sda1. Partition 2 is assigned to /dev/sda8 with a mount point of /media/sda8. The rest of the partitions have a device assignment of /dev/hda5-8 (again, in place of sda5-8) and the hda8 partition cannot be mounted because its mount point conflicts with Partition 2. Adding the appropriate entry for a /media/hda8 mount point appears to solve the last problem. 

So, I thought I'd run it past the group before I filed a bug report, but doesn't this all seem a bit peculiar? Or is this a feature, not a bug?

UPDATE:

Further reflection suggests these issues stem from the newer kernel reverting to the hda vs. sda naming convention for IDE hard drives. Clearly, this can have implications on upgrade. The clean approach, I suppose, is to create new hdaX folders in the /media directory, remount the drives to the new mount points, and edit the fstab to reflect the new arrangement, and finally, after making sure everything works, deleting the now superfluous sdaX folders. I guess upgrades ain't for sissies.

---

