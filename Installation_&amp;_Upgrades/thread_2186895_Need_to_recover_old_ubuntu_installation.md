---
title: "Need to recover old ubuntu installation"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by liuyipei on 2013-11-09
So, I had a functioning dual boot Ubuntu(13.10)/windows7. I am on BIOS.
I first upgraded windows, and Ubuntu disappeared. I then installed a fresh Ubuntu (13.10) on a fresh partition but GRUB still doesn't show up -- Windows just boots everytime without a menu or prompt.

In my attempts to fix things, I did two things:
1. I subsequently used the boot-repair tool to "restore the MBR". 
2. In the meantime I also reinstalled GRUB2 using
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

It is unclear which of the two above actions helped. The fresh installation of Ubuntu is now able to boot, and GRUB is now able to see both the fresh installation of Ubuntu and Windows 7.
However, it is not able to see my old installation. I am able to mount the old partition and see my old files. fdisk, mount, and pastebin information are at the bottom. I would like to recover my old installation.

The two partitions of interest are:
[FONT=system]/dev/sda4[/FONT]   # this partition contains my fresh ubuntu
[FONT=system]/dev/sda5  [/FONT]# this partition contains my old ubuntu, which I need to recover

Interestingly, [FONT=system]I appear to be booting from /dev/sda5[/FONT] (according to fdisk), but **dev/sda4** is mounted at /.
I want to get into a position where I am booting from dev/sda5 and furthermore, **dev/sda5** is mounted at /.  

Thank you so much in advance!


Other observations in boot-repair
In the grub location tab, the *OS to boot by default* dropdown has only two entries; /dev/sda5 is absent.
1. sda4 (current os in use)
2. windows
In the MBR option tab, *partition booted by MBR* drop down has 4 options:
1. sda1 (Windows)
2. sda2 (Windows (boot))
3. sda4 (The OS now in use)
4. sda5 (linux)

Selecting sda5 here, and clicking on apply (i.e. making the changes) does not help, and leads to my current situation where fdisk thinks I am booting from sda5 while I / is mounted to sda4.

Here is my paste url
[http://paste.ubuntu.com/6390127/](http://paste.ubuntu.com/6390127/)

fdisk and mount output are below:

```
[FONT=system]
[FONT=lucida console] yi@zealot:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003f510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1037698700   518745926+   7  HPFS/NTFS/exFAT
/dev/sda3      1037699070  1465147391   213724161    5  Extended
Partition 3 does not start on physical sector boundary.
[B]/dev/sda4      1465147392  1953525167   244188888   83  Linux
/dev/sda5   *  1037699072  1447735295   205018112   83  Linux[/B]
/dev/sda6      1447737344  1465147391     8705024   82  Linux swap / Solaris

yi@zealot:~$ sudo mount
** /dev/sda4 on / type ext4 (rw,errors=remount-ro)**
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=yi)
[/FONT]
[/FONT]
```

*editted for formatting, grammar and clarity of writing.*

---

