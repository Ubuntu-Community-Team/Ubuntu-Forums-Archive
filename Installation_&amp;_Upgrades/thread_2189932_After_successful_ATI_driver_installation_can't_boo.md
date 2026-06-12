---
title: "After successful ATI driver installation can't boot, fglrx is broken, can't fix it"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by igor-iankovych on 2013-11-24
Tried to install ATI driver useing this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) step 3.1 But after successful install stil had no driver istaled, so after reboot tried step 3.2. After that I wasn't able to boot at all. Tried different boot modes and different kernels with no luck. So decided to boot from LiveCD, used chroot to fix my existing instalation. And then I met issue with fglrx.

Output from **apt-get -f install** 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 66.6 MB of archives.
After this operation, 209 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ua.archive.ubuntu.com/ubuntu/ precise-updates/restricted fglrx amd64 2:8.960-0ubuntu1.1 [66.6 MB]
Fetched 66.6 MB in 41s (1,591 kB/s)                                            
sh: 1: cannot create /dev/null: Permission denied
sh: 1: cannot create /dev/null: Permission denied
dpkg-preconfigure: unable to re-open stdin: No such file or directory
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 219600 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1.1_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 61: /var/lib/dpkg/tmp.ci/preinst: cannot create /dev/null: Permission denied
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.960-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/_2%3a8.960-0ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Output from[B] dpkg --configure -a

[/B]```

dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libminiupnpc8 (1.6-precise2) ...
/sbin/ldconfig: 6: /sbin/ldconfig: cannot create /dev/null: Permission denied
/sbin/ldconfig.real: Renaming of /etc/ld.so.cache~ to /etc/ld.so.cache failed: Input/output error
dpkg: error processing libminiupnpc8 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-dev
 libminiupnpc8
 fglrx-amdcccle
```

Output from **apt-get clean** is empty

I've already read and tried a lot of stuff from other similar topics, but it doesn't works for me, and at the and I'm getting the same error. I had the same isses once long time age, but it was during usual (without chroot and LiveCD) session and I've fixed it with advices from other topics (not sure what exact). 

I'm using Ubuntu 12.04.3 x64 and graphics HD6870.

Any help highly appreciated ;)

---

