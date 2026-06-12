---
title: "Freeze when adding a partition to an array (mdadm)"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by castor_fou on 2008-07-02
hello,
I used to install gutsy on raid1 mode (with the alternate cd).
When I have migrated to hardy, something goes wrong.
I can boot my system, but only on one disk. If I try to add the 2nd disk partitions to the array, the box freezes.
And there is nothing in the log.

I have tried to boot on the live cd. I can then install mdadm tools, and recreate the md array with the 1st disk. When I try to add the 2nd disk to the array, the bow freezes as well.
I have tried to zerosuperblock the partitions on the 2nd disk, it doesn't help.

Do you know what is going on ?

---

### Post by dstew on 2008-07-02
> When I have migrated to hardy, something goes wrong.How did you do this? Did you upgrade from inside Gutsy or do a new install of Hardy?

---

### Post by castor_fou on 2008-07-02
I have just updated from inside Gutsy. (something like a new version of ubuntu is available (8.04) button has appeared, and I clicked)

---

### Post by castor_fou on 2008-07-02
ok, I am now in front of my box, I can give details about what I do.
I have 2 disks sda, sdb.
3 arrays in raid 1
md0 (~40Go) for system (lvm inside) with sda3, sdb3
md1 (~300Mo) for boot (ext3) with sda1, sdb1
md2 (~120Go) for data (lvm here) with sda5, sdb5
sda2, sdb2 are for swap

It seems to me that sdb acts weird. I will explain why.
I boot on the hardy live cd. At that step, the arrays are not recognized because raid is not supported out of the box by the livecd.

I install ssh, and start it. All the operations are done from another box.
```
apt-get install ssh
/etc/init.d/ssh start
```
I connect to the ubuntu box via ssh.

I update the packages :
```
apt-get update
```
and install the support for lvm and raid :
```
apt-get install lvm2 dmsetup mdadm
```
at that step, an entry has appeared in /var/log/syslog
```
Jul  2 18:22:30 ubuntu mdadm: DeviceDisappeared event detected on md device /dev/md2
Jul  2 18:22:30 ubuntu mdadm: DeviceDisappeared event detected on md device /dev/md0
Jul  2 18:22:30 ubuntu mdadm: DeviceDisappeared event detected on md device /dev/md1
```

I load the modules
```
modprobe dm-mirror
modprobe dm-mod
```
New entry in /var/log/syslog
```
Jul  2 18:23:41 ubuntu kernel: [  683.864220] device-mapper: uevent: version 1.0.3
Jul  2 18:23:41 ubuntu kernel: [  683.864282] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
```

I am ready to detect existing arrays, at that step mdstat exists and is empty :
```
root@ubuntu:~# cat /proc/mdstat
Personalities :
unused devices: <none>
```

Here I could launch quite an automatic discovery with ```
mdadm --assemble -s
```, but it will freeze the box because of sdb.
Therefore I load the arrays with missing partitions :
```
mdadm --assemble /dev/md0 /dev/sda3
mdadm --assemble /dev/md1 /dev/sda1
mdadm --assemble /dev/md2 /dev/sda5
```

I have now in mdstat :
```
root@ubuntu:~# cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda5[1]
      120005440 blocks [2/1] [_U]

md1 : active raid1 sda1[1]
      289024 blocks [2/1] [_U]

md0 : active raid1 sda3[0]
      39712576 blocks [2/1] [U_]

unused devices: <none>
```

and in syslog :
```
Jul  2 18:27:09 ubuntu kernel: [  891.355077] md: md0 stopped.
Jul  2 18:27:09 ubuntu kernel: [  891.372560] md: bind<sda3>
Jul  2 18:27:09 ubuntu kernel: [  891.436815] md: raid1 personality registered for level 1
Jul  2 18:27:09 ubuntu kernel: [  891.438041] raid1: raid set md0 active with 1 out of 2 mirrors
Jul  2 18:27:09 ubuntu mdadm: DegradedArray event detected on md device /dev/md0
Jul  2 18:27:09 ubuntu kernel: [  891.447592] md: md1 stopped.
Jul  2 18:27:09 ubuntu kernel: [  891.463806] md: bind<sda1>
Jul  2 18:27:09 ubuntu kernel: [  891.528421] raid1: raid set md1 active with 1 out of 2 mirrors
Jul  2 18:27:09 ubuntu mdadm: SparesMissing event detected on md device /dev/md1
Jul  2 18:27:12 ubuntu kernel: [  894.034425] md: md2 stopped.
Jul  2 18:27:12 ubuntu kernel: [  894.078499] md: bind<sda5>
Jul  2 18:27:12 ubuntu kernel: [  894.143343] raid1: raid set md2 active with 1 out of 2 mirrors
Jul  2 18:27:12 ubuntu mdadm: DegradedArray event detected on md device /dev/md2
```

All is quite fine. And the data are there on md0, md1, md2.
However I would like to add sdb3 to md0, sdb1 to md1, sdb5 to md2.

What I have tried is something like :
```
mdadm -v --zero-superblock /dev/sdb1
mdadm -v --add /dev/md1 /dev/sdb1
```
And it directly freezes ubuntu. And it puts nothing in syslog.

2 questions :
1) someone has already met this type of behaviour ?
2) is there a way to better understand what is going on in activating verbose traces ?

any help would be greatly appreciated

---

### Post by castor_fou on 2008-07-04
I have succeeded in connecting the ubuntu box to another one to debug through **netconsole**.
At the time of the freeze, I receive the following messages :
```
 1779.109630] md: recovery of RAID array md1
[ 1779.109652] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 1779.109656] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[ 1779.109680] md: using 128k window, over a total of 289024 blocks.

```
and that's it, it freezes. It was the last message before the death...

---

### Post by castor_fou on 2008-07-04
here is the version of mdadm I use :
```
root@ubuntu:~# mdadm -V
mdadm - v2.6.3 - 20th August 2007
```

---

