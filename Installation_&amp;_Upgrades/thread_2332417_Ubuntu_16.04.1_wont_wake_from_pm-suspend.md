---
title: "Ubuntu 16.04.1 wont wake from pm-suspend"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-07-31
Upgraded from 14.04 the other day.

Tried a pm-suspend, and the system suspended fine.  When I sent a WOL packet, the power light came back and the drives span up, but the system won't talk to me :(

Would not shutdown on press of power button, needed to press/hold power button to force power off.

System is a Zotac NM-10 Intel Atom D525.

Suspend/resume worked on 14.04 (with some problems with the RAID).

Thanks
Dave

---

### Post by David_Partridge on 2016-07-31
Installing upstream kernel 4.6.4 didn't change this behaviour - the system is still locked up after resume.

Dave

---

### Post by David_Partridge on 2016-08-03
I seem to have crash dumps for this which have been submitted AFAICT.

amonra@Charon:~$ ll /var/crash
total 1688K
-rw-r--r-- 1 root whoopsie   1K Aug  3 08:50 kexec_cmd
-rw-r----- 1 root whoopsie 578K Jul 31 17:26 susres.2016-07-31_17:04:36.491243.crash
-rw-r--r-- 1 root whoopsie   0K Jul 31 17:26 susres.2016-07-31_17:04:36.491243.upload
-rw-r----- 1 root whoopsie 584K Jul 31 17:26 susres.2016-07-31_17:25:35.695207.crash
-rw-r--r-- 1 root whoopsie   0K Jul 31 17:26 susres.2016-07-31_17:25:35.695207.upload
-rw-r----- 1 root whoopsie 231K Jul 31 18:35 susres.2016-07-31_18:29:31.427894.crash
-rw-r--r-- 1 root whoopsie   0K Jul 31 18:35 susres.2016-07-31_18:29:31.427894.upload
-rw-r----- 1 root whoopsie 249K Jul 31 18:35 susres.2016-07-31_18:34:12.945029.crash
-rw-r--r-- 1 root whoopsie   0K Jul 31 18:35 susres.2016-07-31_18:34:12.945029.upload
-rw-r----- 1 root whoopsie  35K Aug  3 08:53 susres.2016-08-03_08:51:10.640772.crash
-rw-r--r-- 1 root whoopsie   0K Aug  3 08:56 susres.2016-08-03_08:51:10.640772.upload
amonra@Charon:~$ 

HtH
Dave

---

