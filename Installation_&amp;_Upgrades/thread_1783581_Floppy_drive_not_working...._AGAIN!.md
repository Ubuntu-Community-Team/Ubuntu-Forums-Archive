---
title: "Floppy drive not working.... AGAIN!"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by AKADAP on 2011-06-15
Every time I need to use the floppy drive, I again find it not working.

I have reported this problem before, and it has been fixed before, several times.
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/593140](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/593140)

It is broken again.

Clicking on the "Floppy Drive" item in Nautilus does not even access the drive.

Right clicking and selecting "Detect Media" at least spins the disk, but gives the same non-results regardless of whether there is a disk in the drive.

With no disk in the drive this happens:
```

$ sudo mount /dev/fd0
mount: /dev/fd0 is not a valid block device
$ echo $?
32

```
with a disk in the drive, this happens:
```
$ sudo mount /dev/fd0
$ echo $?
0
$ mount -l
/dev/sde1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/md127 on /morestore/raid1 type ext4 (rw,commit=0) [Home Mirror]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /morestore/raid1/home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
$
```
Mount claims to successfully mount fd0, but it is not actually mounted.

I get the same results on several computers.

Could someone please tell me how to fix this?

It is really embarrassing having to borrow someones Windows computer to read a floppy.

---

### Post by kvv_1986 on 2011-06-15
Hey! I am sorry but I have no idea.

However, check this thread and specifically this post: [http://forums.linuxmint.com/viewtopic.php?f=49&t=50910&start=0#p293191]("http://forums.linuxmint.com/viewtopic.php?f=49&t=50910&start=0#p293191").

It might provide a workaround for your problem.

---

### Post by AKADAP on 2011-06-16
> **kvv_1986 said:**
> Hey! I am sorry but I have no idea.

However, check this thread and specifically this post: [http://forums.linuxmint.com/viewtopic.php?f=49&t=50910&start=0#p293191]("http://forums.linuxmint.com/viewtopic.php?f=49&t=50910&start=0#p293191").

It might provide a workaround for your problem.

That is not a solution to the problem, but it worked well enough for me to get the files I needed off the floppy, Thanks.

---

### Post by AKADAP on 2011-10-17
This is still a problem in 11.10

---

