---
title: "Kubuntu on ICH9R RAID Problem"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2008-03-04
I'm attempting to install Kubuntu 7.10 to be dual booted on an existing Windows
Ultimate system. The system has Intel ICH9R RAID, with a single RAID0 striped
volume, and two partitions, Windows/NTFS and unformatted. I booted from the 
Kubuntu install disk and installed dmraid, but dmraid won't successfully 
activate the RAID volume(s) - see various outputs below.

Appreciate ideas on how to fix ....

$ sudo dmraid -ay
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_dhbacihbbf_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_dhbacihbbf_Volume0" [1/2] on /dev/sdb

$ sudo dmraid -r
/dev/sdb: isw, "isw_dhbacihbbf", GROUP, ok, 488397166 sectors, data@ 0


$ sudo dmraid --debug --verbose -ay
DEBUG: _find_set: searching isw_dhbacihbbf
DEBUG: _find_set: not found isw_dhbacihbbf
DEBUG: _find_set: searching isw_dhbacihbbf_Volume0
DEBUG: _find_set: searching isw_dhbacihbbf_Volume0
DEBUG: _find_set: not found isw_dhbacihbbf_Volume0
DEBUG: _find_set: not found isw_dhbacihbbf_Volume0
DEBUG: checking isw device "/dev/sdb"
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_dhbacihbbf_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_dhbacihbbf_Volume0" [1/2] on /dev/sdb
DEBUG: set status of set "isw_dhbacihbbf_Volume0" to 2
DEBUG: set status of set "isw_dhbacihbbf" to 4
INFO: Activating GROUP RAID set "isw_dhbacihbbf"
DEBUG: freeing devices of RAID set "isw_dhbacihbbf_Volume0"
DEBUG: freeing device "isw_dhbacihbbf_Volume0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_dhbacihbbf"
DEBUG: freeing device "isw_dhbacihbbf", path "/dev/sdb"

---

