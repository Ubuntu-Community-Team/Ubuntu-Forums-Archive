---
title: "Vista 64 is dead, now i want to rescue files on raid 0 (Intel Matrix Storage Manager)"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by bernstar on 2008-09-18
Like the title tells, my Vista has gone. It killed the winlogon.exe and also the Vista-CD is not able to boot right.

So, know i want to switch to a better OS, like ubuntu. But first, i need to rescue my files, but i am not able to. Tried to mount the raid-drives, but only errors.

What i did:

Because lan-driver doesn't work (also not on 8.10 daily), i downloaded and installed dmraid + lib from an other pc. After start, i get the following information:

[INDENT]ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw device for volume "VolumeRAID" broken on /dev/sdb in RAID set "isw_cifcbachbh_VolumeRAID"
ERROR: isw: wrong # of devices in RAID set "isw_cifcbachbh_VolumeRAID" [2/3] on /dev/sdb
ERROR: isw device for volume "VolumeRAID" broken on /dev/sda in RAID set "isw_cifcbachbh_VolumeRAID"
ERROR: isw: wrong # of devices in RAID set "isw_cifcbachbh_VolumeRAID" [2/3] on /dev/sda
ubuntu@ubuntu:~$ dmraid -ay -vvv -d
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdd
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
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
DEBUG: _find_set: searching isw_cifcbachbh
DEBUG: _find_set: not found isw_cifcbachbh
DEBUG: _find_set: searching isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: searching isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: not found isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: not found isw_cifcbachbh_VolumeRAID
NOTICE: added /dev/sdb to RAID set "isw_cifcbachbh"
DEBUG: _find_set: searching isw_cifcbachbh
DEBUG: _find_set: found isw_cifcbachbh
DEBUG: _find_set: searching isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: searching isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: found isw_cifcbachbh_VolumeRAID
DEBUG: _find_set: found isw_cifcbachbh_VolumeRAID
NOTICE: added /dev/sda to RAID set "isw_cifcbachbh"
DEBUG: checking isw device "/dev/sdb"
ERROR: isw device for volume "VolumeRAID" broken on /dev/sdb in RAID set "isw_cifcbachbh_VolumeRAID"
ERROR: isw: wrong # of devices in RAID set "isw_cifcbachbh_VolumeRAID" [2/3] on /dev/sdb
DEBUG: checking isw device "/dev/sda"
ERROR: isw device for volume "VolumeRAID" broken on /dev/sda in RAID set "isw_cifcbachbh_VolumeRAID"
ERROR: isw: wrong # of devices in RAID set "isw_cifcbachbh_VolumeRAID" [2/3] on /dev/sda
DEBUG: set status of set "isw_cifcbachbh_VolumeRAID" to 2
DEBUG: set status of set "isw_cifcbachbh" to 4
INFO: Activating GROUP RAID set "isw_cifcbachbh"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_cifcbachbh_VolumeRAID"
DEBUG: freeing device "isw_cifcbachbh_VolumeRAID", path "/dev/sdb"
DEBUG: freeing device "isw_cifcbachbh_VolumeRAID", path "/dev/sda"
DEBUG: freeing devices of RAID set "isw_cifcbachbh"
DEBUG: freeing device "isw_cifcbachbh", path "/dev/sdb"
DEBUG: freeing device "isw_cifcbachbh", path "/dev/sda"[/INDENT]

Could anybody help me solve the problem. I am new to linux, so please, make the solution as easy as possible. ;-)

Great thanks!

---

