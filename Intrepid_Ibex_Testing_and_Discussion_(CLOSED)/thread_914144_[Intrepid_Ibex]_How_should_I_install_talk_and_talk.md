---
title: "[Intrepid Ibex] How should I install talk and talkd in 8.10 ?"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sycron on 2008-09-08
*actually this is related to ubuntu 8.10 not kubuntu.

I tried installing talkd in Intrepid Ibex. Fist I've installed talk and then talkd. When I've installed talkd I got some nasty errors that i can't know where they come from.

```
sudo apt-get install talkd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  inetutils-inetd
The following NEW packages will be installed:
  inetutils-inetd talkd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.8kB of archives.
After this operation, 291kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/universe inetutils-inetd 2:1.5.dfsg.1-8ubuntu1 [81.9kB]
Get:2 http://archive.ubuntu.com intrepid/universe talkd 0.17-13 [17.9kB]
Fetched 99.8kB in 0s (121kB/s)
Selecting previously deselected package inetutils-inetd.
(Reading database ... 103391 files and directories currently installed.)
Unpacking inetutils-inetd (from .../inetutils-inetd_2%3a1.5.dfsg.1-8ubuntu1_i386.deb) ...
Selecting previously deselected package talkd.
Unpacking talkd (from .../talkd_0.17-13_i386.deb) ...
Processing triggers for man-db ...
Setting up inetutils-inetd (2:1.5.dfsg.1-8ubuntu1) ...
 * Not starting internet superserver: no services enabled.

Setting up talkd (0.17-13) ...
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
```

Thanks for your contribution.

---

