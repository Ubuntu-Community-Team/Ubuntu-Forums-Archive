---
title: "S-L-O-W install (or update)"
date: 2017-09-13
forum: Installation &amp; Upgrades
---

### Post by HankB on 2017-09-13
Hi all,
I'm in the process of installing 16.04.3 on a Dell R420 server. I started yesterday morning so I'm approaching 24 hours. At present the process is still downloading packages (about libproc...) I'm using debootstrap to install so I can install on a ZFS root. I've tested network speed using speedtest.net and I'm getting ~70 Gbs down and 12 Gbs up with ping time about 14 ms. LAN connection seems OK.

I'm installing to two 15K 300GB drives which are on a PERC RAID controller (not configured as RAID drives) and configured as mirrored via ZFS. I copied some files around and disk performance seems stellar. ('dd' w/out disabling buffering reports 1.8 MB/s with -bs=1024K)

Doh. Moot point right now. Later this morning I found the system sitting at the GRUB prompt (from the USB drive) and the following at the ssh prompt from which I was running the install:
```
.
.
.
I: Retrieving libpcre3 2:8.38-3.1
I: Validating libpcre3 2:8.38-3.1
I: Retrieving libpng12-0 1.2.54-1ubuntu1
I: Validating libpng12-0 1.2.54-1ubuntu1
I: Retrieving libpopt0 1.16-10
I: Validating libpopt0 1.16-10
I: Retrieving libprocps4 2:3.3.10-4ubuntu2
I: Validating libprocps4 2:3.3.10-4ubuntu2
I: Retrieving libpython3-stdlib 3.5.1-3
packet_write_wait: Connection to 192.168.1.181 port 22: Broken pipe
hbarta@olive:~$ 

```

I have no idea what led to the crash. This is a retired enterprise server (retired due to age, not operational issues.)

I decided that this was not a good strategy. It is likely that I might have to repeat the installation until I get things working and after 24 hours it didn't even complete once. :( (I'm used to being able to get Linux up and running in about 20 minutes so the 24 hour thing was a surprise.)

I'm working on a different strategy. One nice thing about RAID1 is that it can operate in degraded mode with a single drive. :) I did a normal install with the thought that I'd then configure the second drive for degraded RAID1, copy everything over and then add the first drive to the RAID.

At the moment I'm finishing this post while I wait for 'apt update' to complete. >:( I wonder if this is related to the slowness of 'debootstrap.' I had previously opened the software store and just got the Ubuntu equivalent of a spinning beachball. After several minutes I just closed that. (I usually use 'apt' for managing software anyway.)

Is there something going on with Ubuntu's servers, perhaps as a result of hurricane damage? I'm near Chicago and using Comcast so I'm fairly remote to the part of the country hit by the hurricanes but some times that does not matter.

Thanks!

Edit: This slowdown is really awful. When I boot the live USB and install something it takes many minutes while apt tries to contact archive.ubuntu.com.

Edit.2: Here's what I experience installing a new package:
```
android@androidlx01:~$ time sudo apt install bonnie++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bonnie++
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 67.9 kB of archives.
After this operation, 202 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 bonnie++ amd64 1.97.1 [67.9 kB]
Fetched 67.9 kB in 4min 0s (282 B/s)                        
Selecting previously unselected package bonnie++.
(Reading database ... 212287 files and directories currently installed.)
Preparing to unpack .../bonnie++_1.97.1_amd64.deb ...
Unpacking bonnie++ (1.97.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up bonnie++ (1.97.1) ...

real	4m5.120s
user	0m3.084s
sys	0m0.508s
android@androidlx01:~$ 

```

Most of the time is spent on a line that looks like
```
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)]
```

This is on a brand new install with no changes to sources.list. Is no one else seeing this problem?

Edit.2: Apparently this is a problem using IPV6 and can be resolved by modifying /etc/gai.conf and uncommentiong the line
```
precedence ::ffff:0:0/96  100

```

Easily done by typing
```
sudo vi +54 /etc/gai.conf

```and typing the characters "x:wq" (for those unfamiliar with 'vi'.)

Solution found at 
[http://terokarvinen.com/2016/prefer-ipv4-on-ubuntu-16-04-lts-xenial-etcgai-conf-precedence-ffff0096-100](http://terokarvinen.com/2016/prefer-ipv4-on-ubuntu-16-04-lts-xenial-etcgai-conf-precedence-ffff0096-100)

---

