---
title: "Can't seem to install Gitlab CE on Ubuntu Server 16.04"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by eldarele on 2018-01-30
I'm really new to the entire linux/ubuntu platform.

I'm currently running Ubuntu Server 16.04 LTS with a very simple GUI of core LXDE on top. I've been trying to install Gitlab, so I can set up simple version control.

I've looked on the internet for a solution, and I've tried different solutions, but I couldn't solve my problem. I've updated and upgraded all the packages and Ubuntu can't find any packages left to update or upgrade, so my Ubuntu is all up to date. I've tried installing multiple times, but the packages keeps getting in a bad state, with multiple different errors I've encountered, but I just can't seem to install the package. I've followed every step from this website:
[https://about.gitlab.com/installation/#ubuntu?version=ce](https://about.gitlab.com/installation/#ubuntu?version=ce)

This is the output attemting to install gitlab:

```
user@SVR01:~$ curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  5232    0  5232    0     0   1290      0 --:--:--  0:00:04 --:--:--  1290
user@SVR01:~$ sudo bash script.deb.sh
[sudo] password for user: 
Detected operating system as Ubuntu/xenial.
Checking for curl...
Detected curl...
Running apt-get update... done.
Installing apt-transport-https... done.
Installing /etc/apt/sources.list.d/gitlab_gitlab-ce.list...done.
Importing packagecloud gpg key... done.
Running apt-get update... done.


The repository is setup! You can now install packages.
user@SVR01:~$ sudo apt install gitlab-ce
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gitlab-ce
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 410 MB of archives.
After this operation, 1,211 MB of additional disk space will be used.
Get:1 https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu xenial/main amd64 gitlab-ce amd64 10.4.1-ce.0 [410 MB]
Fetched 286 MB in 5min 36s (849 kB/s)                                                                                                                                                                                                       
Selecting previously unselected package gitlab-ce.
(Reading database ... 117312 files and directories currently installed.)
Preparing to unpack .../gitlab-ce_10.4.1-ce.0_amd64.deb ...
Unpacking gitlab-ce (10.4.1-ce.0) ...
*** Error in `/usr/bin/dpkg': corrupted size vs. prev_size: 0x0000000002a68600 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7fad4ea627e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x7e9dc)[0x7fad4ea699dc]
/lib/x86_64-linux-gnu/libc.so.6(+0x81cde)[0x7fad4ea6ccde]
/lib/x86_64-linux-gnu/libc.so.6(__libc_malloc+0x54)[0x7fad4ea6f184]
/usr/bin/dpkg[0x41d369]
/usr/bin/dpkg[0x418b76]
/usr/bin/dpkg[0x418ced]
/usr/bin/dpkg[0x404d3a]
/usr/bin/dpkg[0x423ade]
/usr/bin/dpkg[0x415e31]
/usr/bin/dpkg[0x406824]
/usr/bin/dpkg[0x403539]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7fad4ea0b830]
/usr/bin/dpkg[0x403649]
======= Memory map: ========
00400000-00443000 r-xp 00000000 fc:00 2759204                            /usr/bin/dpkg
00642000-00643000 r--p 00042000 fc:00 2759204                            /usr/bin/dpkg
00643000-00644000 rw-p 00043000 fc:00 2759204                            /usr/bin/dpkg
00644000-00858000 rw-p 00000000 00:00 0 
01638000-02a9d000 rw-p 00000000 00:00 0                                  [heap]
7fad48000000-7fad48021000 rw-p 00000000 00:00 0 
7fad48021000-7fad4c000000 ---p 00000000 00:00 0 
7fad4d6f7000-7fad4d70d000 r-xp 00000000 fc:00 5767693                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fad4d70d000-7fad4d90c000 ---p 00016000 fc:00 5767693                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fad4d90c000-7fad4d90d000 rw-p 00015000 fc:00 5767693                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fad4d90d000-7fad4db1a000 rw-p 00000000 00:00 0 
7fad4db1a000-7fad4db25000 r-xp 00000000 fc:00 5772374                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
7fad4db25000-7fad4dd24000 ---p 0000b000 fc:00 5772374                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
7fad4dd24000-7fad4dd25000 r--p 0000a000 fc:00 5772374                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
7fad4dd25000-7fad4dd26000 rw-p 0000b000 fc:00 5772374                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
7fad4dd26000-7fad4dd2c000 rw-p 00000000 00:00 0 
7fad4dd2c000-7fad4dd37000 r-xp 00000000 fc:00 5772378                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
7fad4dd37000-7fad4df36000 ---p 0000b000 fc:00 5772378                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
7fad4df36000-7fad4df37000 r--p 0000a000 fc:00 5772378                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
7fad4df37000-7fad4df38000 rw-p 0000b000 fc:00 5772378                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
7fad4df38000-7fad4df4e000 r-xp 00000000 fc:00 5772358                    /lib/x86_64-linux-gnu/libnsl-2.23.so
7fad4df4e000-7fad4e14d000 ---p 00016000 fc:00 5772358                    /lib/x86_64-linux-gnu/libnsl-2.23.so
7fad4e14d000-7fad4e14e000 r--p 00015000 fc:00 5772358                    /lib/x86_64-linux-gnu/libnsl-2.23.so
7fad4e14e000-7fad4e14f000 rw-p 00016000 fc:00 5772358                    /lib/x86_64-linux-gnu/libnsl-2.23.so
7fad4e14f000-7fad4e151000 rw-p 00000000 00:00 0 
7fad4e151000-7fad4e159000 r-xp 00000000 fc:00 5772369                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
7fad4e159000-7fad4e358000 ---p 00008000 fc:00 5772369                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
7fad4e358000-7fad4e359000 r--p 00007000 fc:00 5772369                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
7fad4e359000-7fad4e35a000 rw-p 00008000 fc:00 5772369                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
7fad4e35a000-7fad4e372000 r-xp 00000000 fc:00 5772360                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7fad4e372000-7fad4e571000 ---p 00018000 fc:00 5772360                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7fad4e571000-7fad4e572000 r--p 00017000 fc:00 5772360                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7fad4e572000-7fad4e573000 rw-p 00018000 fc:00 5772360                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7fad4e573000-7fad4e577000 rw-p 00000000 00:00 0 
7fad4e577000-7fad4e57a000 r-xp 00000000 fc:00 5772363                    /lib/x86_64-linux-gnu/libdl-2.23.so
7fad4e57a000-7fad4e779000 ---p 00003000 fc:00 5772363                    /lib/x86_64-linux-gnu/libdl-2.23.so
7fad4e779000-7fad4e77a000 r--p 00002000 fc:00 5772363                    /lib/x86_64-linux-gnu/libdl-2.23.so
7fad4e77a000-7fad4e77b000 rw-p 00003000 fc:00 5772363                    /lib/x86_64-linux-gnu/libdl-2.23.so
7fad4e77b000-7fad4e7e9000 r-xp 00000000 fc:00 5767747                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fad4e7e9000-7fad4e9e9000 ---p 0006e000 fc:00 5767747                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fad4e9e9000-7fad4e9ea000 r--p 0006e000 fc:00 5767747                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fad4e9ea000-7fad4e9eb000 rw-p 0006f000 fc:00 5767747                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fad4e9eb000-7fad4ebab000 r-xp 00000000 fc:00 5772361                    /lib/x86_64-linux-gnu/libc-2.23.so
7fad4ebab000-7fad4edab000 ---p 001c0000 fc:00 5772361                    /lib/x86_64-linux-gnu/libc-2.23.so
7fad4edab000-7fad4edaf000 r--p 001c0000 fc:00 5772361                    /lib/x86_64-linux-gnu/libc-2.23.so
7fad4edaf000-7fad4edb1000 rw-p 001c4000 fc:00 5772361                    /lib/x86_64-linux-gnu/libc-2.23.so
7fad4edb1000-7fad4edb5000 rw-p 00000000 00:00 0 
7fad4edb5000-7fad4edd4000 r-xp 00000000 fc:00 5767764                    /lib/x86_64-linux-gnu/libselinux.so.1
7fad4edd4000-7fad4efd3000 ---p 0001f000 fc:00 5767764                    /lib/x86_64-linux-gnu/libselinux.so.1
7fad4efd3000-7fad4efd4000 r--p 0001e000 fc:00 5767764                    /lib/x86_64-linux-gnu/libselinux.so.1
7fad4efd4000-7fad4efd5000 rw-p 0001f000 fc:00 5767764                    /lib/x86_64-linux-gnu/libselinux.so.1
7fad4efd5000-7fad4efd7000 rw-p 00000000 00:00 0 
7fad4efd7000-7fad4effd000 r-xp 00000000 fc:00 5772359                    /lib/x86_64-linux-gnu/ld-2.23.so
7fad4f055000-7fad4f1ed000 r--p 00000000 fc:00 2753714                    /usr/lib/locale/locale-archive
7fad4f1ed000-7fad4f1f2000 rw-p 00000000 00:00 0 
7fad4f1fb000-7fad4f1fc000 rw-p 00000000 00:00 0 
7fad4f1fc000-7fad4f1fd000 r--p 00025000 fc:00 5772359                    /lib/x86_64-linux-gnu/ld-2.23.so
7fad4f1fd000-7fad4f1fe000 rw-p 00026000 fc:00 5772359                    /lib/x86_64-linux-gnu/ld-2.23.so
7fad4f1fe000-7fad4f1ff000 rw-p 00000000 00:00 0 
7ffe51371000-7ffe51392000 rw-p 00000000 00:00 0                          [stack]
7ffe513b9000-7ffe513bc000 r--p 00000000 00:00 0                          [vvar]
7ffe513bc000-7ffe513be000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I've tried sudo dpkg --configure -a, sudo apt install --reinstall, sudo apt -f install, I've tried removing it with sudo dpkg --remove --force-remove-reinstreq gitlab-ce and install it again, but nothing seems to help.
 If someone could help me with this issue, I would be most grateful!

---

### Post by eldarele on 2018-02-01
Bump

---

