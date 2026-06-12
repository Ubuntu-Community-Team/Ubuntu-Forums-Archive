---
title: "[SOLVED] Update fails on 2.6.24-21, presume prevents distro upgrade to 8.10"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by stir-crazy on 2008-11-09
The kernel update "linux-ubuntu-modules-2.6.24-21-generic" fails repeatedly from Adept Updater, giving the fllowing error message:

```
There was an error commiting changes. Possibly there was a problem
downloading some packages or the commit would break packages.

```

From terminal, either sudo apt-get upgrade sudo apt-get -f upgrade yields:


```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-ubuntu-modules-2.6.24-21-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5433kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 245681 files and directories currently installed.)
Preparing to replace linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32 (using .../linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_i386.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.24-21-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/firmware/2.6.24-21-generic/ipw2200-ibss.fw')
Errors were encountered while processing:
 /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Apparently unable to upgrade the distro to Intrepid until this is resolved, but have no idea what I might need to do to fix this. :confused:

Searching the forums here, looks like the 2.6.24-21 kernel upgrade is fairly iffy itself, though obviously many have been able to apply it, and it has been appearing in adept notifier for well over a week now.

Pointers please.  Thanks!

---

### Post by stir-crazy on 2008-11-09
Deleted the file from /var/cache/apt/archives per this thread, which got the updates to install.  Per this thread [http://ubuntuforums.org/showthread.php?t=728914&highlight=broken+pipe&page=2](http://ubuntuforums.org/showthread.php?t=728914&highlight=broken+pipe&page=2)


Don't seem to be able to apply a distro upgrade now though, maybe after a reboot.

---

