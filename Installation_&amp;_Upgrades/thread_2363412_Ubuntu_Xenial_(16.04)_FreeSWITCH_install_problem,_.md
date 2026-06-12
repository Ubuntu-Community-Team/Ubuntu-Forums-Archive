---
title: "Ubuntu Xenial (16.04) FreeSWITCH install problem, could not locate package"
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by arunk5051 on 2017-06-09
I am new to Linux and I have been trying to install FreeSWITCH on Ubuntu 16.04 using these instructions: [https://freeswitch.org/confluence/display/FREESWITCH/Ubuntu+16.04+Xenial](https://freeswitch.org/confluence/display/FREESWITCH/Ubuntu+16.04+Xenial), but, I have been unable to install it correctly. I will post the output from the terminal below: 
Any help will be thankful.

arun@ubuntu:/$ sudo wget -O - [https://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/freeswitch_archive_g0.pub](https://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/freeswitch_archive_g0.pub) |sudo apt-key add -
[sudo] password for arun:
--2017-06-09 14:45:20--  [https://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/freeswitch_archive_g0.pub](https://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/freeswitch_archive_g0.pub)
Resolving files.freeswitch.org (files.freeswitch.org)... 209.105.235.7, 2607:f348:1021::7
Connecting to files.freeswitch.org (files.freeswitch.org)|209.105.235.7|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1796 (1.8K)
Saving to: &#8216;STDOUT&#8217;

-                              100%[====================================================>]   1.75K  --.-KB/s    in 0s      

2017-06-09 14:45:21 (36.9 MB/s) - written to stdout [1796/1796]

OK
arun@ubuntu:/$ sudo echo "deb [http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/](http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/) xenial main" > /etc/apt/sources.list.d/freeswitch.list
arun@ubuntu:/$ sudo apt-get update && sudo apt-get install -y freeswitch-meta-vanilla
Hit:1 [http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable](http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable) xenial InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]                                                 
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]        
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Fetched 306 kB in 1s (217 kB/s)                             
Reading package lists... Done
W: [http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/dists/xenial/InRelease:](http://files.freeswitch.org/repo/ubuntu-1604/freeswitch-unstable/dists/xenial/InRelease:) Signature by key 9C0CADF0911F534CC19C218C018DDB2EF14D5181 uses weak digest algorithm (SHA1)
Reading package lists... Done
Building dependency tree       
Reading state information... Done

E: Unable to locate package freeswitch-meta-vanilla

---

