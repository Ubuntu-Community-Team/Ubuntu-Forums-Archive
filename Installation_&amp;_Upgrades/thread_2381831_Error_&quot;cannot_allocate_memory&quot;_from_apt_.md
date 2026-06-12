---
title: "Error &quot;cannot allocate memory&quot; from apt upgrade"
date: 2018-01-05
forum: Installation &amp; Upgrades
---

### Post by George Heine on 2018-01-05
Recently got an error when trying to do a routine upgrade,  Here's the output:

```
2018-01-05 
$ echo 'Y' | sudo aptitude upgrade
The following packages will be upgraded:
  firefox firefox-locale-en initramfs-tools initramfs-tools-bin
  libruby1.9.1 r-cran-mass ruby1.9.1
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.0 MB of archives. After unpacking 1,024 B will be freed.
Do you want to continue? [Y/n/?] Writing extended state information...
Get: 1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main initramfs-tools all 0.103ubuntu4.10 [44.6 kB]
Get: 2 http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu/ trusty/ r-cran-mass 7.3-48-1trusty0 [1,100 kB]
Get: 3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main initramfs-tools-bin i386 0.103ubuntu4.10 [8,626 B]
Get: 4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox i386 57.0.4+build1-0ubuntu0.14.04.1 [45.4 MB]
Get: 5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox-locale-en i386 57.0.4+build1-0ubuntu0.14.04.1 [692 kB]
Get: 6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libruby1.9.1 i386 1.9.3.484-2ubuntu1.6 [2,691 kB]
Get: 7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main ruby1.9.1 i386 1.9.3.484-2ubuntu1.6 [35.5 kB]
Fetched 50.0 MB in 9min 33s (87.1 kB/s)
(Reading database ... 2107315 files and directories currently installed.)
Preparing to unpack .../initramfs-tools_0.103ubuntu4.10_all.deb ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
$
```

Any ideas as to what caused this?  
Running Ubuntu 14.04, soon to upgrade to Mint 18.3.  Maybe this will be impetus to do it sooner.

thanks for any help -

---

### Post by oldos2er on 2018-01-05
How much physical RAM does the computer have? And do you have a swap file or partition? If so, what size are they?

---

### Post by George Heine on 2018-01-05
Computer is a Dell Optiplex GX-20 with 1GB of physical RAM.  There is a swap partition, also 1GB.   
Got this system four years ago and have run apt upgrade 100-200 times with no previous problems.

---

### Post by oldos2er on 2018-01-05
I would try increasing your swap to 2GB (or more) if possible.

---

### Post by George Heine on 2018-01-16
Thank you for your suggestion.  Increased swap partition to 4 GB, upgrade went through without errors.  
Question: is there a way of determining, before running the upgrade, how much memory will be required?

---

### Post by oldos2er on 2018-01-16
Not that I'm aware of (assuming you really mean RAM and not hard disk space). Perhaps someone else knows.

---

