---
title: "upadte for upgrade from 6.10 to 7.04 fails."
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by caffienefree on 2007-05-15
I only have ssh access to the machine I'm attempting to upgrade. In attempting to execute the command sudo apt-get update (before doing sudo apt-get dist-upgrade) I receive the output below. The machine has internet access as I can ping multiple addresses.

> 
4% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fo
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [2275B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages [14B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [1989B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources [1408B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [20B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [2035B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Error reading from server - read (104 Connection reset by peer)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages [1007kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages [20B]
2% [13 Packages 26064/1007kB 2%] [Connecting to us.archive.ubuntu.com (91.189.8
gzip: stdin: unexpected end of file
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
  Sub-process gzip returned an error code (1)
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [1885B]
23% [15 Sources gzip 0] [13 Packages 240368/1007kB 23%] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Sub-process gzip returned an error code (1)
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages [20B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources [1266B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7628B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [148kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [3754kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources [1710B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [6509B]
0% [22 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.31)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages [14B]
0% [Connecting to archive.ubuntu.com (91.189.88.31)]                476kB/s 10s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources [2599B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages [1307kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7866B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [193kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [4912kB]
43% [30 Packages gzip 0] [Waiting for headers]           481kB/s 49710d 6h28m3s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources [385kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources [1567B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources [63.5kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [20B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources [2345B]
41% [35 Sources gzip 0]                                  481kB/s 49710d 6h28m2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 1162kB in 21s (54.3kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
***Now it's the same thing on different servers, for a bit, so I snipped it out***
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Does anyone have any ideas regarding this issue? I've searched around, but it doesn't seem as if any have had a similar problem (As far as I can tell). Thank you in advance.

---

### Post by gwoodard on 2007-05-15
Tell me How much memory you have, Hard Drive Space, Internet Connection (dial-up or broadband) and then we can go on from there

---

### Post by caffienefree on 2007-05-15
Dell Optiplex GX260. 512 MB ram, 20 GB drive. I believe it's a T1 line used for the campus, but I'm not positive. 

Updating and upgrading HAS worked in the past. It's only recently that it's throwing this at me.

---

### Post by gwoodard on 2007-05-16
What is the size of each partition, you may just not have enough room to upgrade so you might have to (big might) clean the HD or get a bigger one

You may need to download and burn an ISO of 7.04 and burn it to a CD then reinstall Ubuntu, If there is any programs you want to keep I can't help on that

---

