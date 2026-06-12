---
title: "Disable TMPFS"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by holysword on 2015-12-17
Hi, I would like to know how can I totally and completely disable TMPFS from my system. I want my /tmp to be mounted on a physical hard disk.

Thanks in advance.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

---

### Post by ubfan1 on 2015-12-17
/tmp is normally just a directory under the root (/), so it's probably on the hard disk.  TMPFS is not even used for /tmp.  Some things like /run are kept in ram and use TMPFS (show this with the command df -a in a terminal), but that does not seem to be what you are asking.

---

### Post by holysword on 2015-12-18
> **ubfan1 said:**
> /tmp is normally just a directory under the root (/), so it's probably on the hard disk.  TMPFS is not even used for /tmp.  Some things like /run are kept in ram and use TMPFS (show this with the command df -a in a terminal), but that does not seem to be what you are asking.

True, /tmp is mounted in the harddrive, sorry about that. This is output of cat /etc/mtab | grep tmpfs
none /sys/fs/cgroup tmpfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0

and this is df -h             
/dev/sda6       103G   21G   78G  21% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,9G  4,0K  1,9G   1% /dev
tmpfs           384M  1,3M  382M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,9G  884K  1,9G   1% /run/shm
none            100M   14M   87M  14% /run/user
AFS             2,0T     0  2,0T   0% /afs

so if I understand it correctly, whatever is inside /run is allowed to take up to 1,9G of my memory (please, correct me if I am wrong) if needed be. I would like to be able to control and/or completely disable that.

---

### Post by ian-weisser on 2015-12-18
> **holysword said:**
> I would like to be able to control and/or completely disable that.

You probably can, but it won't be easy. /run uses tmpfs for a reason.

A good place to start is [https://wiki.debian.org/ReleaseGoals/RunDirectory](https://wiki.debian.org/ReleaseGoals/RunDirectory)
and [http://unix.stackexchange.com/questions/13972/what-is-this-new-run-filesystem](http://unix.stackexchange.com/questions/13972/what-is-this-new-run-filesystem)

---

### Post by ubfan1 on 2015-12-18
You looked at the wrong line, /run is only 1.3M  not 1.9G.

---

