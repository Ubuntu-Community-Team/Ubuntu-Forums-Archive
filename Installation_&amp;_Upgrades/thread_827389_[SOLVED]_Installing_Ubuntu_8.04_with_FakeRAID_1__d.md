---
title: "[SOLVED] Installing Ubuntu 8.04 with FakeRAID 1 : dmraid -ay returning nothing"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by netangel on 2008-06-12
Hello Ubuntu users,

I'm trying to install Ubuntu 8.04 Hardy Heron on my Dell DIMENSION 9200 on which I already have a double-boot Gutsy with Windows XP configured with FadeRAID 1. (Actually I want to install Hardy erasing totally my Gutsy)

Following [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) , I installed dmraid.
But, when trying dmraid -ay, the command returns nothing.

```
ubuntu@ubuntu:~$ sudo dmraid -ay
ubuntu@ubuntu:~$ sudo dmraid -ay
```
What's strange is that I can see my RAID ARRAY :
```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: isw, "isw_dhaebbabbd", GROUP, ok, 488281248 sectors, data@ 0
/dev/sda: isw, "isw_dhaebbabbd", GROUP, ok, 488281248 sectors, data@ 0
```

My system log is telling me that the device-mapper can't map my disks to /dev/mapper/isw...
```
ubuntu@ubuntu:~$ tail -n 2 /var/log/syslog 
Jun 12 21:45:12 ubuntu kernel: [ 3739.367739] device-mapper: table: 254:0: mirror: Device lookup failure
Jun 12 21:45:12 ubuntu kernel: [ 3739.367746] device-mapper: ioctl: error adding target to table
```

So I followed [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) and here are the debug information :
```
ubuntu@ubuntu:~$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: isw metadata discovered
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_dhaebbabbd
DEBUG: _find_set: not found isw_dhaebbabbd
DEBUG: _find_set: searching isw_dhaebbabbd_ARRAY
DEBUG: _find_set: searching isw_dhaebbabbd_ARRAY
DEBUG: _find_set: not found isw_dhaebbabbd_ARRAY
DEBUG: _find_set: not found isw_dhaebbabbd_ARRAY
NOTICE: added /dev/sdb to RAID set "isw_dhaebbabbd"
DEBUG: _find_set: searching isw_dhaebbabbd
DEBUG: _find_set: found isw_dhaebbabbd
DEBUG: _find_set: searching isw_dhaebbabbd_ARRAY
DEBUG: _find_set: searching isw_dhaebbabbd_ARRAY
DEBUG: _find_set: found isw_dhaebbabbd_ARRAY
DEBUG: _find_set: found isw_dhaebbabbd_ARRAY
NOTICE: added /dev/sda to RAID set "isw_dhaebbabbd"
DEBUG: checking isw device "/dev/sda"
DEBUG: checking isw device "/dev/sdb"
DEBUG: set status of set "isw_dhaebbabbd_ARRAY" to 16
DEBUG: set status of set "isw_dhaebbabbd" to 16
INFO: Activating GROUP RAID set "isw_dhaebbabbd"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_dhaebbabbd_ARRAY"
DEBUG: freeing device "isw_dhaebbabbd_ARRAY", path "/dev/sda"
DEBUG: freeing device "isw_dhaebbabbd_ARRAY", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_dhaebbabbd"
DEBUG: freeing device "isw_dhaebbabbd", path "/dev/sda"
DEBUG: freeing device "isw_dhaebbabbd", path "/dev/sdb"
```
```
ubuntu@ubuntu:~$ sudo dmraid -b
/dev/sdb:    488281250 total, "5QE1Y4E7"
/dev/sda:    488281250 total, "5QE1Y4CV"
```

Can somebody help me ?

---

### Post by netangel on 2008-06-12
I finally found my answer here : [http://ubuntuforums.org/showthread.php?t=593109](http://ubuntuforums.org/showthread.php?t=593109)

The problem was as I had a previous install of Ubuntu, it swapped on when the liveCD started.
```
ubuntu@ubuntu:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	3903752	0	-1
/dev/sdb6                               partition	3903752	0	-2
```
So I resolved the problem with
```
ubuntu@ubuntu:~$ sudo swapoff -a
```
Then ...
```
ubuntu@ubuntu:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
ubuntu@ubuntu:~$ sudo dmraid -ay
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_dhaebbabbd_ARRAY" already active
RAID set "isw_dhaebbabbd_ARRAY1" already active
RAID set "isw_dhaebbabbd_ARRAY2" already active
RAID set "isw_dhaebbabbd_ARRAY3" already active
RAID set "isw_dhaebbabbd_ARRAY5" already active
RAID set "isw_dhaebbabbd_ARRAY6" already active
```
Yeeeapeee !

---

