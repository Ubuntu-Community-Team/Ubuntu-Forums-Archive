---
title: "cryptic dpkg errors"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2010-08-04
I've often come across this error, but have never really found a guide that succinctly deals with the issue:

```
#sudo apt-get upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ntp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/517kB of archives.
After this operation, 217kB of additional disk space will be used.
(Reading database ... 40144 files and directories currently installed.)
Preparing to replace ntp 1:4.2.4p4+dfsg-7ubuntu5.2 (using .../ntp_1%3a4.2.4p8+dfsg-1ubuntu2_i386.deb) ...
 * Stopping NTP server ntpd                                                                               [ OK ] 
ln: creating symbolic link `/etc/apparmor.d/force-complain/usr.sbin.ntpd': No such file or directory
dpkg: error processing /var/cache/apt/archives/ntp_1%3a4.2.4p8+dfsg-1ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
 * Starting NTP server ntpd                                                                               [ OK ] 
Errors were encountered while processing:
 /var/cache/apt/archives/ntp_1%3a4.2.4p8+dfsg-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've seen this error relate to a number of packages, ranging from mysql to fglrx & beyond.
In this case it related to NTP. I assumed that the downloaded archive was somehow corrupted, so I deleted the cache (/var/cache/apt/archives/ntp_1%3a4.2.4p8+dfsg-1ubuntu2_i386.deb) & manually downloaded a fresh copy from the main achive & tried manually installing it with gpkg, but I still get he same result.

Other than starting to start digging around in the code/install scripts, there is very little in the way of information provided that I can use to ascertain the cause of the issue & how to go about addressing the issue.
The basic gist of these errors are usually along the lines of: 
```

dpkg: error processing /var/cache/apt/archives/{SOME PACKAGE}.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
 * Starting {SOME Daemon}                                                                               [ OK ] 
Errors were encountered while processing:
 /var/cache/apt/archives/{SOME PACKAGE}.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Sometimes this sort of error can cause any subsequent upgrade/install attempts to fail.

I pity the poor n00b that has just switched over to Linux/Ubuntu, so their 1st round of upgrades & their system gets borked, of no fault of their own..... (I mean, really, what does "error code 1" mean in the real world?)

Is there some sort of guide or series of tests/steps to take to get beyond this point?

---

