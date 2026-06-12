---
title: "CD Rom problems"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by Sageth on 2010-09-19
After 2 days of working on this, I fully admit that I don't know what else to do.  Here's the scoop:

Rather than actually learn how to use fstab, I installed ubuntu and then installed MountManager to get my networked NAS to automount on startup.  Well, this destroyed my CD Rom.  I can boot off the CD, but I cannot get it to properly recognize the drive.  Here's my current fstab (which will, from now on be backed up before any changes):

```
sage@sage-desktop:~$ cat /etc/fstab
UUID=6e28ed53-2421-4de1-a65f-47e00c9efbd8 /media/data_drive ext4 defaults 0 0
UUID=5305e4d4-8374-4e70-8218-40d6fa954f82 / ext4 defaults 0 1
/dev/sr0 /media/cdrom udf,iso9660 users,noauto 0 0
UUID=5c7395fd-6be9-4395-825e-7bda1159e863 swap swap sw,noauto 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 users,noauto 0 0
UUID=0fabe63b-3364-4362-9509-c293a4e18b4a /media/image_drive ext4 defaults 0 0

```

/dev/sr0 and sr1 are my two CD drives, and while this now gets them to mount, they don't seem to be able to properly read CD's and they can't write at all (I assume that I need to add ",rw" at the end of them.)  

I also get some errors flash up right before the login screen appears, but it's too fast for me to be able to see, but I don't remember seeing them before mountmanager was used. 

Just some additional information:
```
sage@sage-desktop:~$ ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2010-09-19 15:38 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-09-19 15:38 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-09-19 15:38 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-09-19 15:38 /dev/dvdrw -> sr0

```

```
sage@sage-desktop:~$ for d in cd dvd;do ls -l /dev/dvd|grep -i $d;done
lrwxrwxrwx 1 root root 3 2010-09-19 15:38 /dev/dvd -> sr0

```

Can anyone help me get my CD's back to normal?  I'd appreciate it eternally.

---

### Post by Sageth on 2010-09-21
I've reinstalled ubuntu 10.04 from scratch.  DVD still isn't working.  Any ideas at all?  I can't even mount them from the command line and if I click on the icons in "Computer" they don't do anything (not even an error).

Here's some additional information:
```
sage@sage-desktop:/mnt$ ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/cdrom1 -> sr1
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/cdrw1 -> sr1
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/dvd1 -> sr1
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/dvdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-09-21 00:21 /dev/dvdrw1 -> sr1

```But, I get this error on both /sr0 and /sr1:
```
sage@sage-desktop:/mnt$ sudo hdparm -I /dev/sr0
/dev/sr0:
HDIO_DRIVE_CMD(identify) failed: Invalid exchange
```And finally, my new fstab (dvd's are not there by default.. I added them):
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ad09eea5-9cfc-4828-ba14-f3aa497cb057 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5c7395fd-6be9-4395-825e-7bda1159e863 none            swap    sw              0       0
#Other drives
UUID=6e28ed53-2421-4de1-a65f-47e00c9efbd8    /media/data_drive    ext4    defaults    0    2
UUID=0fabe63b-3364-4362-9509-c293a4e18b4a    /media/image_drive    ext4    defaults    0    2
UUID=5305e4d4-8374-4e70-8218-40d6fa954f82    /            ext4    defaults    0    0
#CDROM Drive(s)
/dev/sr0 /media/dvd0 iso9660,udf user,noauto,exec,utf8 0 0
/dev/sr1 /media/dvd1 iso9660,udf user,noauto,exec,utf8 0 0

```

---

### Post by Sageth on 2010-09-22
Am I in the wrong forum for this?  I really have no idea what to do next.  Do the messages above suggest hardware incompatibility? Is there something I need to install?  Do I need to repost this somewhere else?

I've since found a few other posts that suggest blacklisting the floppy and not having the cd be the first boot device.  I've done both of them and now the drive will mount a cd once, but then it disappears and doesn't work anymore.  Also, once it's mounted, I can't do anything with it... I can see the files, but can't interact with them.

I've also rem'd out the cd rom statements as suggested in another post?

---

### Post by Sageth on 2010-09-24
Well, after days of this, I found the problem, though I don't know how to permanently fix it.  There's a conflict on having 2 DVD's on my system.  As a last resort, I unplugged one of them and now it's working fine.  Not sure how to get it to actually work with both of them, but I'll deal with that at another point.

---

