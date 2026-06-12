---
title: "dpkg error code (1)"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by christossmail on 2013-11-17
Hi everyone,

I am trying to install snort on 12.04 32-bit server i have been able to use apt-get to install other programs but not snort.  actually that is not true, when i run sudo apt-get install snort i did get all of the config files but not the actual program.   this is the error i get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  snort-doc
The following NEW packages will be installed:
  snort
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/696 kB of archives.
After this operation, 1,794 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 87984 files and directories currently installed.)
Unpacking snort (from .../snort_2.9.2-3ubuntu1_i386.deb) ...
usermod: user snort is currently logged in
dpkg: error processing /var/cache/apt/archives/snort_2.9.2-3ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 8
Errors were encountered while processing:
 /var/cache/apt/archives/snort_2.9.2-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i have gone thru the typical google search and tried things like apt-get -f, apt-get upgrade,  apt-get autoclean, apt-get remove --purge getdeb-repository, i even installed it on my desktop to find out which repository snort is on and added it to the server, norhting is working.  any suggestions?

Thanks in advance for any input you can give

---

### Post by ian-weisser on 2013-11-18
Seems very similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/snort/+bug/1031917](https://bugs.launchpad.net/ubuntu/+source/snort/+bug/1031917)
I recommend you subscribe to that bug, and use the "affects me too" button.

---

