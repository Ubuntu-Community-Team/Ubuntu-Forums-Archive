---
title: "Question About RAID1 and LVM Setup"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by mark-phillipsoasis on 2014-09-18
I recently purchased a shiny new System 76 laptop with two 1 TB SSDs. I wanted to set up the beast using LVM and RAID1. I re-installed the system using the server version of 14.04 so I could have the installer create the raid and lvm. I followed this blog post - [http://blog.miketoscano.com/?p=307](http://blog.miketoscano.com/?p=307), and the steps in the installer to create the raid and then the lvm, and then install the OS, and it all seemed to work. I then installed the ubuntu-desktop and then the system76 drivers. It all seems to be working. 

However, I cannot find mdadm. It does not appear to be installed. I looked at /etc/fstab and I see
```
mark@tsunami:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg1_tsunami-root /               ext4    errors=remount-ro 0       1
/dev/mapper/vg1_tsunami-swap none            swap    sw              0       0

```

And the free space shows
```
mark@tsunami:~$ df -h
df: ‘/run/user/107/gvfs’: Permission denied
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/vg1_tsunami-root  1.8T  120G  1.6T   7% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          7.8G  4.0K  7.8G   1% /dev
tmpfs                         1.6G  1.2M  1.6G   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          7.8G  144K  7.8G   1% /run/shm
none                          100M   40K  100M   1% /run/user

```

There is no mdadm.conf.
```
mark@tsunami:~$ sudo locate mdadm
[sudo] password for mark: 
/usr/share/bash-completion/completions/mdadm

```

And mdstat does not seem correct from what I have read.
```
mark@tsunami:~$ cat /proc/mdstat
Personalities : 
unused devices: <none>

```

Am I missing something? Do I really have what I intended to install?

Thanks!

Mark

---

