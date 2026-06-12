---
title: "XFS Mounting Problem / Use ext3?"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by djseto on 2007-04-15
I am trying to mount a 2nd SATA 500GB drive. When I use Gparted, it formats the drive to XFS successfully, however, when I try to add it to my FSTAB, I first need a UUID to identify the drive. If I use "tune2fs -l /dev/sdb", i get an error saying:

 "Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock." 


After some googling, I ran xfs_repair, but it could not find the "Superblock" (I have no idea what that actually is). I can mount the drive using the mount command, but without the UUID, which I can't get from tune2fs, I can't add it to the FSTAB table so that it automounts.

If I format the drive as ext3, I can get a UUID just fine. My concerns are:

A) Is there something physically wrong with my drive causing me to not be able to have a "good" Superblock
B) Since I am using this for MythTV, I want good I/O speed and I heard that XFS is the way to go. If I can't get this to work, will ext3 work fine? I don't know much about any other formats and really only know about these two based on some MythTV install guides.

Thanks

---

### Post by newlinux on 2007-04-15
Can't help with the XFS problem, but I use ext3 for recordings in my mythbackends (QAM/ATSC/NTSC) and it works fine. I just have the delete files slowly option set in myth.

As far as UUID goes, I usually do:

ls -l /dev/disk/by-uuid 

to get the UUID. Don't know if your situation is different.

---

### Post by majoridiot on 2007-04-15
one of my mythmedia hds is a 320GB sata that i formatted to xfs.  i didn't worry mucking about with the UUID, etc.
i just let the system work it out for itself. all i did was:

make a mount point: in this case /media/sdb1
give ownership of the mount point to mythtv
edit /etc/fstab and added:
> /dev/sdb1  /media/sdb1 xfs defaults 0 0

and on the next reboot, the system sussed out the uuid and straightened out fstab to its liking.

---

### Post by djseto on 2007-04-15
Ill have to try that tomorrow. How do you give MythTV ownership to that mount point? Im still learning Linux as I go...

thanks

---

### Post by majoridiot on 2007-04-15
```
$ sudo chown -R mythtv:mythtv /media/sdb1
```

will do it recursively, to include all files and directories sdb1 might contain. (-R is the recursive option)

---

### Post by djseto on 2007-04-16
That did it. Thanks!

---

### Post by majoridiot on 2007-04-16
glad you got it working! :D

---

### Post by ViRMiN on 2007-04-16
As you're using XFS and not EXT2/EXT3, xfs_admin was the utility you would have needed.  To display the UUID of /dev/sdb1 you could've done:

```
sudo xfs_admin -u /dev/sdb1
```

---

### Post by djseto on 2007-04-16
ah. Thanks. Definitely gotta write this one down.

---

### Post by ViRMiN on 2007-04-16
Yeah, even though you fixed your problem, I thought you might like to have some extra info for future reference.  Check out the man pages for more info though!

---

