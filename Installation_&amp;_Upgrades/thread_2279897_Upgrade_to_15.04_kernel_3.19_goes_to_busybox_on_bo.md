---
title: "Upgrade to 15.04 kernel 3.19 goes to busybox on boot, 3.16 boots fine"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by Jimmie Aaron Butler on 2015-05-26
I have full disk encryption.  On boot with 3.19 boot goes into busybox, boot with 3.16 starts fine.

dmesg from busybox gives an error like 
```
EXT4-fs: couldn't mount as ext3 due to feature incompatibilities
```

fstab 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>/dev/mapper/ubuntu--vg-root /               ext4    defaults,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID='1fa1afc7-f57e-4fe0-b2eb-91fbfc7011da' /boot           ext2    defaults        0       2
```

mount (from 3.16)
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=8146020k,nr_inodes=2036505,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1632460k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime,stripe=4)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1632460k,mode=700,uid=1000,gid=1000)
/home/.ecryptfs/jimmie/.Private on /home/jimmie type ecryptfs (rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=4f174ac7e1a3b690,ecryptfs_sig=30be66c2b4fcbf5f,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```


I'm sure you need more information, let me know what additional information is needed.

Thanks in advance.

---

