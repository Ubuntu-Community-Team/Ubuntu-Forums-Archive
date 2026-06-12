---
title: "Disk partition icon missing from Feisty desktop"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by bw44 on 2007-10-15
The FAT32 data sharing partition isn't on the desktop.

This is my first post to ubuntu forums.  I wasn't sure whether to post to "General"
or to "Installation and Upgrade."  Since I only got ubuntu (Feisty) to boot for the
first time yesterday, I decided it was an "installation" problem.  I searched the
forums for an answer, but the only one that seemed related I didn't understand.
(Sorry if it's been answered already!)

Below is the output from "cat /etc/fstab" and "fdisk -l" (saw these were
asked for in replies to other posts):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3499dd4f-c968-44aa-8502-e8fbe48c6510 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D3-0411  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=0220769520769001 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=90BA-89AA  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=daf95157-41e9-4d06-b69d-86abb8fd4489 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        2193    17583142+   7  HPFS/NTFS
/dev/sda3            2194        3409     9767520   83  Linux
/dev/sda4            3410        3738     2642692+   5  Extended
/dev/sda5            3532        3738     1662727+   b  W95 FAT32
/dev/sda6            3410        3530      971869+  82  Linux swap / Solaris

On my desktop there is an icon for "Dell Utility" and another for "sda2"
which are the Dell-installed Fat16 primary partition and the Windows XP
NTFS partition.

But shouldn't there also be an icon for the "W95 FAT32" partition, which
I created during installation to share data between Windows and ubuntu?
(Does it have to do with the fact it's a logical, not primary partition?)

Can someone please tell me how to to make an icon for the FAT32 partition
appear on the desktop (and how to make the other two disappear (if I don't
need them)?

Any help would be much appreciated.

---

### Post by Pumalite on 2007-10-15
Check in Places>Home(left column)

---

### Post by bw44 on 2007-10-15
Thanks for the prompt reply, but the FAT32 disk (partition) is not shown
either under Places or under Places> Home, which  shows:

Desktop
File System
Floppy Drive
sda2
DellUtility

Any other thoughts?

---

### Post by Pumalite on 2007-10-15
Check in /media
Also post the output of:
mount

---

### Post by bw44 on 2007-10-15
No joy in /media.

Output from  mount:

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda5 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Looks like it's there (/dev/sda5), but being an almost complete Linux novice
I don't know how to make it appear on the desktop.

I appreciate your help!

---

### Post by bw44 on 2007-10-15
I think I've found a place where my question is answered.

I installed ubuntu using the alternate CD following the very helpful and detailed
instructions provided at:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

(many thanks to their author -- without whom I'd probably still be trying to install
instead of posting this message from a working system!)

In those instruction he/she says to set the mount point for the FAT32 data  sharing
partition as /windows.  I followed the instructions but had no idea what they really
meant.  Now I see why it is mounted in my system in that directory.  I'm not sure
if it would have been possible (or desirable) to enter it manually as /media 
rather than /windows.

Anyway, there's a whole discussion at the same site:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

where the author explains the process of mounting the shared FAT32 partition.

I'm still not clear whether it's possible or a good idea to put the partition in /media but
when I've had some sleep I'll try and figure it out.

Sorry I didn't read all the documentation I had before posting my question.

If the forum moderator wants to mark this thread closed that would be ok by me.

Cheers.

---

