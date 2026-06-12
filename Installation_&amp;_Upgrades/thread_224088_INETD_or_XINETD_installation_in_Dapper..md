---
title: "INETD or XINETD installation in Dapper."
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by crazygluesniffer on 2006-07-27
I am currently trying to install VMWare server on my Ubuntu 6.06 Desktop installation but it will not finish configuration because the INETD or XINETD (referred to as 'super server' by VMWare) are not installed (by default in Ubuntu I understand).

I have beat my head against the wall trying to install from command line and Synaptic but I am so new to Linux I can figure out how to get either of them to install.  

When I run an apt-get install xinetd command I get the following:

   Package xinetd is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
   E:  Package xinetd has no installation canidate

Please any help getting this installed would be very much appreciated, I've read many posts referring to similiar issues but I've found nowhere that is having the same problem I am.  Please help a n00b migrate from Windows.

---

### Post by nwgray on 2006-08-10
I had the same problem. I did this:

sudo gedit /etc/apt/sources.list

I enabled every deb source (I got a few errors but nothing stopped it)
did a sudo apt-get update
and then sudo apt-get install xinetd. 

Here's the install - 

sudo apt-get install xinetd
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xinetd
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 131kB of archives.
After unpacking 356kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main xinetd 1:2.3.14-0ubuntu1 [131kB]
Fetched 131kB in 0s (365kB/s)
Selecting previously deselected package xinetd.
(Reading database ... 158169 files and directories currently installed.)
Unpacking xinetd (from .../xinetd_1%3a2.3.14-0ubuntu1_i386.deb) ...
Setting up xinetd (2.3.14-0ubuntu1) ...
Stopping internet superserver: xinetd.
Adding `diversion of /etc/init.d/inetd to /etc/init.d/inetd.real by xinetd'
Starting internet superserver: xinetd.


Hope this helps!

---

