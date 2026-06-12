---
title: "shared folder (windows,Linux) on ntfs partition not working"
date: 2018-10-26
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2018-10-26
I'm running Ubuntu 18.04.1 LTS on a Toshiba Laptop with dual boot.  I want to share documents folder with both systems.

The partition mounts, and the permissions are set correctly, and everything looks fine, but as soon as I try to open a file or save a file I get this error message:
> Error when getting information for file “/home/MyDocuments”:  Transport endpoint is not connected., and I cant even open the  /home folder

note: currently my windows10 won't boot, because it was in hibernation mode, and I'm still (after a month) working on getting the problem fixed so I can boot windows 

fstab:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installationuN
UUID=bbcfa370-972b-40a3-9602-7db31bc47a8e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=6afb7ff8-3d2c-4f47-86f6-f8458a7ce1bc /home           ext4    defaults        0       2
# /home/MyDocuments was on /dev/sda6 during installation

UUID=5CD7D62C79361B95 /home/MyDocuments ntfs-3g   permissions     0       1
# /home/Windows10 was on /dev/sda1 during installation

UUID=F6B4C7B8B4C77A1F /home/Windows10    ntfs-3g   permissions     0       1
# /home/windows7 was on /dev/sda2 during installation
UUID=C470EDD770EDD06A /home/windows7  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=2a4c7082-92ca-4898-8694-7a575ce61ce0 none            swap    sw              0       0

laast lines of output from ```
mount
.
.
.

/dev/sda8 on /home type ext4 (rw,relatime,data=ordered)
/dev/sda6 on /home/MyDocuments type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
/dev/sda2 on /home/windows7 type fuseblk (ro,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
/dev/sda1 on /home/Windows10 type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=392604k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```:

---

### Post by TheFu on 2018-10-26
Linux doesn't work with NTFS file systems that aren't properly closed.  There are many guides about that.

There are settings for inside Windows to disable fastboot (or whatever MSFT decided to call it this year) and  don't hibernate/suspend any storage you want to access from outside Windows.  Both these things don't properly close the file system.  The NTFS driver should refuse to mount, but if it doesn't, expect data corruption.

For NTFS mounts, you probably need to specify the uid= and gid= options along with big_writes for performance. For single-user systems, this is fine. The mount.ntfs manpage has more details.

I use 
```
#!/bin/bash
UID=1000
GID=1000
LABEL1=300G
LABEL2=250G
LABEL3=400G
OPT1="big_writes,uid=$UID,gid=$GID"

 mkdir -p /mnt/$LABEL1 /mnt/$LABEL2 /mnt/$LABEL3
 mount -o $OPT1 LABEL=$LABEL1 /mnt/$LABEL1
 mount -o $OPT1 LABEL=$LABEL2 /mnt/$LABEL2
 mount -o $OPT1 LABEL=$LABEL3 /mnt/$LABEL3
 rmdir  /mnt/$LABEL1 /mnt/$LABEL2 /mnt/$LABEL3

```

You can add in -t ntfs to the OPT1 settings, if you like.

gvfs is slow, BTW. Best to avoid it for mounts you plan to use a bunch.  Sure, for those very occasional needs, it is fine, but performance suffers.

From the manpage:```

       big_writes
              This option prevents fuse from splitting write buffers  into  4K
              chunks,  enabling  big  write buffers to be transferred from the
              application in a single step (up to some system limit, generally
              128K bytes).

```

There is a way to map specific Windows userids to Linux uids according to the manpage.  I've never done that. I really should check that out. Seems simple for a fairly static setup.  Could be a nightmare in a corporate env.

---

### Post by Morbius1 on 2018-10-26
> UUID=5CD7D62C79361B95 /home/MyDocuments ntfs-3g   [COLOR=#0000cd]**permissions**[/COLOR]     0       1
Oh dear.

The [COLOR=#0000cd]**permissions**[/COLOR] option allows you in Linux to set ownership and permissions on individual files on an ntfs file system. 

That is not the standard way Linux mounts an ntfs partition and has only been suggested by people who have never used it or used it for an isolated ntfs partition in a Linux only setup and not with a dual boot.

The Windows system has no idea what all these Linux users and their permissions are so it has to be done very very carefully. In essence setting up translation tables that tells the system that "bill" on Linux with this uid is "bill" on Windows with the corresponding sid.

It's madness.

It sounds like you never got write access to this partition which means the gods are with you. At a minimum replace **permissions** with **defaults**.

You have another issue with hibernation as discussed above by TheFu.

---

