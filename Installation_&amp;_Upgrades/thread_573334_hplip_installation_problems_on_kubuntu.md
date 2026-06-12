---
title: "hplip installation problems on kubuntu"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by g.a. on 2007-10-11
Hi,

I'm using kubuntu 7.04

I'm trying to install an HP Color Laserjet3600n that is in a Windows network. After several tries I can see the printer but there is not its specific driver. I tried the 3000 or 3700 models but it did not work.

I'm trying to install hplip (yes, it was already there but I unistalled somewhen...) and I'm getting an error of the kind "Sub-process /usr/bin/dpkg returned an error code".

I'm reading posts from this morning and I tried a little bit everything, in particular I tried to force the installation, to upgrade apt-get, etc.

Here is my full shell output, any suggestion is warmly, warmly welcomed:

root@neo:/usr/share/hplip# apt-get install hplip
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  hpijs-ppds hplip-doc
Recommended packages:
  hpijs
The following NEW packages will be installed:
  hplip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/620kB of archives.
After unpacking 2843kB of additional disk space will be used.
Selecting previously deselected package hplip.
(Reading database ... 112447 files and directories currently installed.)
Unpacking hplip (from .../hplip_1.7.3-0ubuntu1_i386.deb) ...
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail]
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

