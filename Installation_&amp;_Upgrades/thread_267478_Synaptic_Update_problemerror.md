---
title: "Synaptic Update problem/error"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by Carbonfish on 2006-09-28
Hi all,

I got an update notification in my system panel so I went to Synaptic, reloaded, marked all updates (there were two), and applied the updates. They downloaded, and started to install, but then I got the error message that you can see in my screenshot.

I have tried a couple of different times to download and install this update with no success. I even went into a terminal and tried to install the update through Aptitude, but it said the the file couldn't be found.

A little help??

TIA,

Kent

---

### Post by Carbonfish on 2006-09-28
Hi again,

Here is a follow up after I tried to upgrade and install using apt-get.
(see screenshot below)

If anyone has any suggestions I would appreciate them as I really don't want to live with this update notification in my system panel for the rest of my life.  ;) 

Thanks,

KC

---

### Post by Carbonfish on 2006-09-28
I am sure that I named this wrong, and that is why nobody is jumping in to help me here.

I tried to upgrade my way out of this problem in the Terminal, but all I got was this:

carbonfish@carbonfish-laptop:~$ sudo apt-get clean
Password:
carbonfish@carbonfish-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Fetched 3B in 2s (1B/s)
Reading package lists... Done
carbonfish@carbonfish-laptop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
carbonfish@carbonfish-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0 libdns21
  libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4 libnss3
  libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssl
22 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 54.5MB of archives.
After unpacking, 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71 .2kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1 .1 [373kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libssl0.9.8 0.9.8a-7ubuntu 0.2 [2594kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisc11 1:9.3.2-2ubuntu1. 1 [172kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libdns21 1:9.3.2-2ubuntu1. 1 [478kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccc0 1:9.3.2-2ubuntu1 .1 [90.4kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccfg1 1:9.3.2-2ubuntu 1.1 [102kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libbind9-0 1:9.3.2-2ubuntu 1.1 [91.0kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main liblwres9 1:9.3.2-2ubuntu1 .1 [107kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main bind9-host 1:9.3.2-2ubunt u1.1 [108kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main dnsutils 1:9.3.2-2ubuntu1 .1 [175kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox-gnome-support 1.5 .dfsg+1.5.0.7-ubuntu0.6.06 [75.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnspr4 2:1.firefox1.5.d fsg+1.5.0.7-ubuntu0.6.06 [147kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnss3 2:1.firefox1.5.df sg+1.5.0.7-ubuntu0.6.06 [670kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.7- ubuntu0.6.06 [7925kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libxfont1 1:1.0.0-0ubuntu 3.2 [216kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25  [23.4kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-26-386  2.6.15-26.47 [21.7MB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-mo dules-common 2.6.15.11-5 [17.9kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-mo dules-2.6.15-26-386 2.6.15.11-4 [8138kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main mozilla-thunderbird 1.5.0 .7-0ubuntu0.6.06 [10.3MB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssl 0.9.8a-7ubuntu0.2  [976kB]
Fetched 54.5MB in 31m5s (29.2kB/s)
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5- 12ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
carbonfish@carbonfish-laptop:~$ sudo apt-get install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
carbonfish@carbonfish-laptop:~$


Any and all help welcome. I *really* don't want to have to start from scratch.

I used the "simple backup" utility in the Admin drop-down, but that may have done more harm than good.

Thanks for your input (I hope).

KC

---

