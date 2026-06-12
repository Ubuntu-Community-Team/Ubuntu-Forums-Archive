---
title: "Update and upgrade issues"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Huss on 2010-07-15
Hi all,

I am having trouble upgrading and updating.

When updating the file downloads to 99% and then stops. The error message is: 
```
 Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
```

And then for the upgrade:

```

:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-2.6.31-22-generic
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libvte-common libvte9
  linux-generic linux-image-generic python-vte
10 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.2MB/40.2MB of archives.
After this operation, 90.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com karmic-updates/main linux-image-2.6.31-22-generic 2.6.31-22.60 [28.9MB]
Err http://au.archive.ubuntu.com karmic-updates/main libc-bin 2.10.1-0ubuntu17 
  Bad header line
Get:2 http://security.ubuntu.com karmic-security/main libc-bin 2.10.1-0ubuntu17 [715kB]
2% [2 libc-bin 705184/715kB 98%] [Waiting for headers]

```

I believe this has something to do with a power outage while upgrading a few days ago. Most of the install completed after rebooting, all except the three 'linux kernel image' files and a few others. 

Also, as a side issue, Flash plugin and Flex builder are no longer working. This may be unrelated.

Does any one have any trouble shooting advice for the issue?

Thanks for reading.

Cheers

Huss

---

### Post by Huss on 2010-07-15
A quick update:
I rebooted again and the upgrade is now working. I'm not sure if this will fix my Adobe related problems, but it's progress.

---

