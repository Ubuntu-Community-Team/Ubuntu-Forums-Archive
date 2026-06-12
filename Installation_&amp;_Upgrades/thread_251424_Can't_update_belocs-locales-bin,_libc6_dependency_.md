---
title: "Can't update: belocs-locales-bin, libc6 dependency issue"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by wyth on 2006-09-05
I've run into a broken package problem with belocs-locales-bin, libc6, and locales.  

Whenever I try to update or install a new package, I have a broken package: beloc-locales-bin.  And it seems I can't configure belocs-locales-bin until libc6 is installed, but I can't install libc6 without having configured belocs-locales-bin.

When I try to install libc6, I get:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  libc6
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4588kB of archives. After unpacking 10.2MB will be used.
Writing extended state information... Done
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 2303 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.3.6-0ubuntu20_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
dpkg: error processing /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of belocs-locales-bin:
 belocs-locales-bin depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
dpkg: error processing belocs-locales-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on belocs-locales-bin (>= 2.3.5-5ubuntu1); however:
  Package belocs-locales-bin is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 belocs-locales-bin
 locales


And I get the same sort of thing when I try to install belocs-locales-bin:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  libc6
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4588kB of archives. After unpacking 10.2MB will be used.
Do you want to continue? [Y/n/?] yes
Writing extended state information... Done
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 2303 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.3.6-0ubuntu20_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
dpkg: error processing /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of belocs-locales-bin:
 belocs-locales-bin depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
dpkg: error processing belocs-locales-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on belocs-locales-bin (>= 2.3.5-5ubuntu1); however:
  Package belocs-locales-bin is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 belocs-locales-bin
 locales
joe@Eisteoir:~$ sudo dpkg --configure belocs-locales-bin
dpkg: dependency problems prevent configuration of belocs-locales-bin:
 belocs-locales-bin depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
 belocs-locales-bin depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing belocs-locales-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 belocs-locales-bin
  

If I try to fix broken packages through Synaptic, I get:

> E: /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb: subprocess pre-installation script returned error exit status 1

I'm hoping there's a way around this, as I've been using this system for months with no problems and would rather not re-install (although all critical data is backed up).  My system is working, it's just not updatable at this point.  And I've gone through [ubuntu_demon's broken depency how to here]("http://www.ubuntuforums.org/showthread.php?t=186672"), but that hasn't done it.

Any help will be so greatly appreciated.

---

### Post by wyth on 2006-09-05
I know it's only been 2 hours, but I don't want this to be the fifth question I've never had a response to.  Don't let me down, folks, I know there's gotta be someone out there with some info on this.

---

### Post by wyth on 2006-09-05
B
U
M
P

---

