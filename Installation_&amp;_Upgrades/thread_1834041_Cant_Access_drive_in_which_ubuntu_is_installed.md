---
title: "Cant Access drive in which ubuntu is installed"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by nachiappantce on 2011-08-26
Hi All,

Need a help with Ubuntu Wubi installation, I have windows in c: and now i have newly installed Ubuntu in c: through Wubi
Now I see only my d: in ubuntu, How to access c: ? Can someone help me with this ? I am pasting the o/p of mount command.
Thanks in advance..


/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,all ow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nachi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nachi)

---

### Post by bcbc on 2011-08-27
Alt-F2, /host
Ctrl-D to bookmark

With wubi, the drive you install to is always the host and is mounted as /host.

---

