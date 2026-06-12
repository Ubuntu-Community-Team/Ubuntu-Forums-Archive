---
title: "Btrfs in Ubuntu 9.10"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Joseph Smith on 2009-11-14
[SIZE=3][COLOR=Blue]So how do I enable btrfs in the Ubuntu 9.10 installer? 

Btrfs is not listed as an option in the list of available file systems during partitioning.
Do I have to pass some special command when booting the Live CD?

I did a search all over the forum but was unable to find an answer to this specific question.[/COLOR][/SIZE]

---

### Post by falconindy on 2009-11-14
btrfs is still unstable (subject to change) and isn't included as an option during install. I'm not even sure the Ubuntu kernel includes btrfs.

---

### Post by Joseph Smith on 2009-11-14
[SIZE=3][COLOR=Blue]If the kernel in 9.10 includes btrfs, there should be some secret command to enable it in the installer. I remember reading that in Fedora you had to pass "icantbelieveitsnotbtrfs" to the installation program during boot-up. 

I am aware of the unstable state of btrfs, but I am willing to take a risk and experiment.[/COLOR][/SIZE]

---

### Post by falconindy on 2009-11-14
This is the results of cat /proc/filesystems on my 10.04 VM:
```
nodev	sysfs
nodev	rootfs
nodev	bdev
nodev	proc
nodev	cgroup
nodev	cpuset
nodev	tmpfs
nodev	debugfs
nodev	securityfs
nodev	sockfs
nodev	usbfs
nodev	pipefs
nodev	anon_inodefs
nodev	inotifyfs
nodev	devpts
	ext3
	ext2
	ext4
nodev	ramfs
nodev	hugetlbfs
nodev	ecryptfs
nodev	fuse
	fuseblk
nodev	fusectl
nodev	mqueue
	reiserfs
nodev	vboxsf
nodev	binfmt_misc
```
It's not in the kernel.

---

### Post by Joseph Smith on 2009-11-14
[SIZE=3][COLOR=Blue]Eh...how are people supposed to test btrfs in Ubuntu, when the developers do not even include it in the kernel? :-(

By the way, I do not see xfs and jfs either in that list you provided, but those two file systems have been available in Ubuntu for a long time.

Something is not right.
[/COLOR][/SIZE]

---

### Post by osx on 2009-11-17
Any update on this subject? I, too, would like to start testing btrfs.

---

### Post by osx on 2009-11-18
I noticed there is a package (not installed by default) called btrfs-tools in Ubuntu 9.10. Does this enable the option to use the btrfs file system in Ubuntu?

By the way, great article on btrfs here [http://www.linux-mag.com/id/7308/](http://www.linux-mag.com/id/7308/)

---

### Post by osx on 2009-11-18
> **Joseph Smith said:**
> [SIZE=3][COLOR=Blue]Eh...how are people supposed to test btrfs in Ubuntu, when the developers do not even include it in the kernel? :-(

By the way, I do not see xfs and jfs either in that list you provided, but those two file systems have been available in Ubuntu for a long time.

Something is not right.
[/COLOR][/SIZE]
Joseph,

I posted some information you may find useful. According to this site [http://packages.ubuntu.com/karmic/btrfs-tools](http://packages.ubuntu.com/karmic/btrfs-tools) it does appear that installing the btrfs-tools package will allow you to convert an ext3 filesystem to btrfs. I plan on trying this out on a virtual machine.

---

### Post by bugslayr on 2010-01-27
Hello!
I also played with btrfs on an external disk ... 
After installing btrfs-tools you can create file systems via /usr/bin/mkfs.btrfs.
See /usr/bin/btrfs* and the man pages for btrfsck btrfsctl btrfs-image  btrfs-show  for additional info.

To my knowledge the pseudo file /proc/filesystems lists the file systems supported by the currently running kernel. You probably have to load the btrfs module to use the file system.

If you want to boot from a btrfs device, you might have to tweak the kernel and/or ram disk to have support at boot time.

I hope this helps!
    Martin

---

