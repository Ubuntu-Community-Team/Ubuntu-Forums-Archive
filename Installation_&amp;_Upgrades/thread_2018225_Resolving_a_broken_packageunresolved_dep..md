---
title: "Resolving a broken package/unresolved dep."
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by patagriff on 2012-07-06
Running Ubuntu 11.10, I tried to resolve unresolved dependencies using    sudo apt-get -f install     resulting in the following:


patrick@patrick-Aspire-5515:~$ sudo apt-get -f install
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ifupdown
Suggested packages:
  rdnssd
The following packages will be upgraded:
  ifupdown
1 upgraded, 0 newly installed, 0 to remove and 1339 not upgraded.
1 not fully installed or removed.
Need to get 53.5 kB of archives.
After this operation, 50.2 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ifupdown i386 0.7.1ubuntu1 [53.5 kB]
Fetched 53.5 kB in 1s (43.0 kB/s)   
(Reading database ... 238016 files and directories currently installed.)
Preparing to replace ifupdown 0.7~alpha5.1ubuntu5.1 (using .../ifupdown_0.7.1ubuntu1_i386.deb) ...
Unpacking replacement ifupdown ...
dpkg: error processing /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_i386.deb (--unpack):
 trying to overwrite '/etc/init.d/networking', which is also in package netbase 5.0ubuntu1
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/ifupdown_0.7.1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
            -------------------------------------
Synaptic Package Mgr solution was to remove 129 packages of the 716 I just updated, which I thought too drastic. ANY SUGGESTIONS WOULD BE APPRECIATED.

Sincerely,
P. Griffith

---

### Post by dino99 on 2012-07-06
want to know : 11.10 or quantal ?  (quantal/main ifupdown i386 0.7.1ubuntu1)

---

