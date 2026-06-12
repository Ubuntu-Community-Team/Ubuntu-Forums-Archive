---
title: "Need help upgrading from 5.10 to 6.06"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by rav on 2006-07-31
i did as written in the form "updating from the cd 6.06" and it is not  update any help . I am new please help me. when i did these error came. Please help me!

ravi@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday 31 May 2006 08:46:20 AM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.


ravi@ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [45.5kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [25.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
98% [21 Sources gzip 0]                                              9005B/s 5s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 3276kB in 8m34s (6362B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by OpsVentus on 2006-07-31
It looks like the cd is corrupted.
You can check by booting from the disk and select the check option on boot.
If so: try to download again, check the download with the hash(if you know how), burn again, and check again.

Cheers,
Bart.

---

### Post by rav on 2006-07-31
sir i have ordered 5 6.06 lts cd from shipit . I am getting this error and can not install. It would be nice if the cd has upgrade options.

---

### Post by rav on 2006-07-31
sir i have ordered 5 6.06 lts cd from shipit . I am getting this error and can not install. It would be nice if the cd has upgrade options.

And where is yhe link for the order of "Alternate Install CD".
Please provide the link as the internet speed is very low at my place.

---

### Post by OpsVentus on 2006-07-31
Sorry, didn't read the output good enough.
The problem is not the cd, but it wants to download the index file's from the internet, that fails.
Sins you have got a cd you do not need internet to upgrade. So we can comment the lines in sources.list for the internet repository's. This way it will skip that part and hopefully will upgrade.

In terminal type:
sudo gedit /etc/apt/sources.list
Now you see all the sources apt-get/synaptic use.
Infront of every line starting with "http://" put an #.
Then try the 'apt-get update' command again.
Now it will not download the index from the internet.

Cheers,
Bart.

ps. the alternate install CD is not ship't, you have to download it. But it will not solve this problem.

---

