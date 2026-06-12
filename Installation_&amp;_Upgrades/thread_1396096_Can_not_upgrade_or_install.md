---
title: "Can not upgrade or install"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by OldGamer on 2010-02-01
I am currently running a small headless home server with ubuntu 8.04.  I have had it set up and running for a while, and once or twice a week, I will ssh in and do an apt-get update and upgrade.  However, the last time that I tried to do this, I got disconnected from the wireless in the middle, and since then I have not been able to upgrade. 

```
michael@home-server:/media$ sudo apt-get upgrade
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisc35 libisccfg30 liblwres30
  linux-image-server linux-server
The following packages will be upgraded:
  base-files fuse-utils grub klibc-utils libfuse2 libklibc python2.5
  python2.5-minimal samba samba-common samba-doc
11 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/18.5MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.8_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `ed': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.8_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 
I get the same error, regardless of whether or not I try to upgrade, or install a new package.  After searching the net, I have tried 'dpkg --configure -a' but get absolutely no output.  I have deleted the .deb files and redownloaded them.  I have tried to clean, autoremove and many others.  I finally decided to connect the monitor to the server, and I found I had errors in my root partition.  I booted with an ubuntu rescue disc, and ran fsck on the partition, and it found and corrected many errors.  But after I reboot into the normal OS, all the errors come back.  I am hoping that I don't have to reinstall the whole server, because I am happy with the set up that I have now.  If it comes down to that, I guess I would probably have to put a new hard drive in it.  Before I do that, I was hoping that someone on here might know of something I overlooked or didn't try.  Maybe it is an easy fix, and I just haven't been able to find it yet.  Thanks in advance for any replies!

OldGamer

---

### Post by gnack on 2010-02-01
Looks like it's trying to tell you there something wrong with the "ed" (line-oriented editor) package.  Have you tried something like:

```

cd /var/lib/dpkg/info
sudo rm ed.list
sudo apt-get --reinstall install ed

```

If so, the output of running:

```

sudo dpkg --unpack /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.8_i386.deb

```

would help (it might have more details that apt-get isn't passing along)

---

### Post by OldGamer on 2010-02-01
Wow!  I have just spent hours searching for the answer to this on the internet, and was pretty much ready to just give it up.  But your suggestion worked perfectly.  Thanks a million!  This is just one of the many reasons that I love ubuntu and this forum.

OldGamer

---

