---
title: "upgrading error"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2016-04-23
Upgrading from 15.10 to 16.04 on my Dell M50 was not straightforward. First it stopped with a bunch of errors, so I ran 'dpkg --configure -a' and finally it appears to be OK, except for one error that occurs doing a regular dist-upgrade:

```
Reading package lists... Done                      Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libjpeg-turbo-progs
The following packages will be upgraded:
  libjpeg-progs
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/71.4 kB of archives.
After this operation, 160 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 302158 files and directories currently installed.)
Preparing to unpack .../libjpeg-progs_1%3a9b-1_i386.deb ...
Unpacking libjpeg-progs (1:9b-1) over (8c-2ubuntu8) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg-progs_1%3a9b-1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/rdjpgcom', which is also in package libjpeg-turbo-progs 1.3.0-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-progs_1%3a9b-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I appreciate your help.

Daniel

---

### Post by bapoumba on 2016-04-24
That % in the file name is not normal. Please try to reinstall libjpeg-progs : ```
sudo apt-get install --reinstall libjpeg-progs
```

---

### Post by danielsender on 2016-04-24
It didn't work, see the transaction:
```
sudo apt-get install --reinstall libjpeg-progsReading package lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libjpeg-progs
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/71.4 kB of archives.
After this operation, 160 kB of additional disk space will be used.
(Reading database ... 302158 files and directories currently installed.)
Preparing to unpack .../libjpeg-progs_1%3a9b-1_i386.deb ...
Unpacking libjpeg-progs (1:9b-1) over (8c-2ubuntu8) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg-progs_1%3a9b-1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/rdjpgcom', which is also in package libjpeg-turbo-progs 1.3.0-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-progs_1%3a9b-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2016-04-25
The packages **libjpeg-progs** and **libjpeb-turbo-progs** *conflict* and cannot both be installed on your 16.04 system at the same time.

---

### Post by danielsender on 2016-04-25
that's what I thought, so which one is the recommended one for 16.04?

---

### Post by ian-weisser on 2016-04-25
Looking at the control files using apt-cache, seem like libjpeg-turbo-progs replaces libjpeg-progs.

---

### Post by danielsender on 2016-04-25
These two packages were dwelling happily on 14.04 but the upgrade from 14.04 to 16.04 brought the problem. The response to 'dpkg -l | grep jpeg' was a line indicating that libjpeg-progs was some kind of transitional packages related to the requirements. As you suggested I purged that package and I was able to run the upgrade.

Thank you very much.

---

### Post by oldos2er on 2016-04-25
Could you please mark the thread as 'Solved' under the Thread Tools menu at the top of this page. Doing so helps others who might be having the same problem.

Thanks!

---

