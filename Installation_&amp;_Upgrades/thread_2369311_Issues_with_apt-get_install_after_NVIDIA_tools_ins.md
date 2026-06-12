---
title: "Issues with apt-get install after NVIDIA tools install (no installation candidate)"
date: 2017-08-21
forum: Installation &amp; Upgrades
---

### Post by softwaregoddess2 on 2017-08-21
Hello All,
I am running 16.04 LTS and everything was fine until  I installed the tools for the NVIDIA Jetson TX1 and switched by display driver to NVIDIA. Since this I have been unable to install packages or do updates. I have tired to install several packages to no avao; but the one I am now using as a test case is 'git'.

Here is a list my current source list:

```


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.atlantic.net/ubuntu/ xenial main restricted
deb-src http://mirror.atlantic.net/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.atlantic.net/ubuntu/ xenial-updates main restricted
deb-src http://mirror.atlantic.net/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.atlantic.net/ubuntu/ xenial universe
deb-src http://mirror.atlantic.net/ubuntu/ xenial universe
deb http://mirror.atlantic.net/ubuntu/ xenial-updates universe
deb-src http://mirror.atlantic.net/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.atlantic.net/ubuntu/ xenial multiverse
deb-src http://mirror.atlantic.net/ubuntu/ xenial multiverse
deb http://mirror.atlantic.net/ubuntu/ xenial-updates multiverse
deb-src http://mirror.atlantic.net/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://mirror.atlantic.net/ubuntu/ xenial-security main restricted
deb-src http://mirror.atlantic.net/ubuntu/ xenial-security main restricted
deb http://mirror.atlantic.net/ubuntu/ xenial-security universe
deb-src http://mirror.atlantic.net/ubuntu/ xenial-security universe
deb http://mirror.atlantic.net/ubuntu/ xenial-security multiverse
deb-src http://mirror.atlantic.net/ubuntu/ xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src  http://archive.canonical.com/ubuntu xenial partner
```

I have tried a source.list without the canonicals sections and using the us.archive.ubuntu.com/ubuntu with the same results.

The original source.list.d directory looked like this:
```
cuda-8-0-local.list
cuda-8-0-local.list.save
graphics-drivers-ubuntu-ppa-xenial.list
graphics-drivers-ubuntu-ppa-xenial.list.save
libopencv4tegra-repo.list
libopencv4tegra-repo.list.save
visionworks-repo.list
visionworks-repo.list.save
visionworks-sfm-repo.list
visionworks-sfm-repo.list.save
visionworks-tracking-repo.list
visionworks-tracking-repo.list.save
xorg-edgers-ubuntu-ppa-xenial.list
xorg-edgers-ubuntu-ppa-xenial.list.save

```

It was throwing error and talking a long time with with the visionworks repos, so I shorted the list down to:
 
```
org-edgers-ubuntu-ppa-xenial.list
xorg-edgers-ubuntu-ppa-xenial.list.save
```.

I have pinged and verified my gateway.
I haver verified that git and git-core are in  [http://mirror.atlantic/net/ubuntu/pool/main/g](http://mirror.atlantic/net/ubuntu/pool/main/g)

I have tried the apt-get clean, apt-get-update, apt-get-upgrade and apt-get dist-upgrade combination. The results are below: The only odd thing I can see is that is can't find the arm64 that was added with the NVIDIA installation.

```
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ sudo apt-get clean
[sudo] password for softwaregoddess: 
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libllvm3.8
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ sudo apt-get update
Get:1 http://mirror.atlantic.net/ubuntu xenial InRelease [247 kB]
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:3 http://mirror.atlantic.net/ubuntu xenial-updates InRelease [102 kB]      
Get:4 http://mirror.atlantic.net/ubuntu xenial-security InRelease [102 kB]     
Hit:5 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu xenial InRelease         
Get:6 http://mirror.atlantic.net/ubuntu xenial/main Sources [868 kB]
Get:7 http://mirror.atlantic.net/ubuntu xenial/restricted Sources [4,808 B]
Get:8 http://mirror.atlantic.net/ubuntu xenial/universe Sources [7,728 kB]
Get:9 http://mirror.atlantic.net/ubuntu xenial/multiverse Sources [179 kB]
Get:10 http://mirror.atlantic.net/ubuntu xenial/main amd64 Packages [1,201 kB]
Get:11 http://mirror.atlantic.net/ubuntu xenial/main i386 Packages [1,196 kB]
Ign:12 http://mirror.atlantic.net/ubuntu xenial/main arm64 Packages
Get:13 http://mirror.atlantic.net/ubuntu xenial/main Translation-en [568 kB]
Get:14 http://mirror.atlantic.net/ubuntu xenial/restricted amd64 Packages [8,344 B]
Get:15 http://mirror.atlantic.net/ubuntu xenial/restricted i386 Packages [8,684 B]
Get:16 http://mirror.atlantic.net/ubuntu xenial/restricted Translation-en [2,908 B]
Get:17 http://mirror.atlantic.net/ubuntu xenial/universe amd64 Packages [7,532 kB]
Get:18 http://mirror.atlantic.net/ubuntu xenial/universe i386 Packages [7,512 kB]
Ign:19 http://mirror.atlantic.net/ubuntu xenial/universe arm64 Packages
Get:20 http://mirror.atlantic.net/ubuntu xenial/universe Translation-en [4,354 kB]
Get:21 http://mirror.atlantic.net/ubuntu xenial/multiverse amd64 Packages [144 kB]
Get:22 http://mirror.atlantic.net/ubuntu xenial/multiverse i386 Packages [140 kB]
Ign:23 http://mirror.atlantic.net/ubuntu xenial/multiverse arm64 Packages
Get:24 http://mirror.atlantic.net/ubuntu xenial/multiverse Translation-en [106 kB]
Get:25 http://mirror.atlantic.net/ubuntu xenial-updates/main Sources [270 kB]
Get:26 http://mirror.atlantic.net/ubuntu xenial-updates/restricted Sources [3,012 B]
Get:27 http://mirror.atlantic.net/ubuntu xenial-updates/universe Sources [168 kB]
Get:28 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse Sources [7,232 B]
Get:29 http://mirror.atlantic.net/ubuntu xenial-updates/main amd64 Packages [620 kB]
Get:30 http://mirror.atlantic.net/ubuntu xenial-updates/main i386 Packages [596 kB]
Ign:31 http://mirror.atlantic.net/ubuntu xenial-updates/main arm64 Packages
Get:32 http://mirror.atlantic.net/ubuntu xenial-updates/main Translation-en [252 kB]
Get:33 http://mirror.atlantic.net/ubuntu xenial-updates/restricted amd64 Packages [7,804 B]
Get:34 http://mirror.atlantic.net/ubuntu xenial-updates/restricted i386 Packages [7,804 B]
Get:35 http://mirror.atlantic.net/ubuntu xenial-updates/restricted Translation-en [2,548 B]
Get:36 http://mirror.atlantic.net/ubuntu xenial-updates/universe amd64 Packages [517 kB]
Get:37 http://mirror.atlantic.net/ubuntu xenial-updates/universe i386 Packages [497 kB]
Ign:38 http://mirror.atlantic.net/ubuntu xenial-updates/universe arm64 Packages
Get:39 http://mirror.atlantic.net/ubuntu xenial-updates/universe Translation-en [202 kB]
Get:40 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse amd64 Packages [15.5 kB]
Get:41 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse i386 Packages [14.6 kB]
Ign:42 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse arm64 Packages
Get:43 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse Translation-en [7,540 B]
Get:44 http://mirror.atlantic.net/ubuntu xenial-security/main Sources [87.9 kB]
Get:45 http://mirror.atlantic.net/ubuntu xenial-security/restricted Sources [2,604 B]
Get:46 http://mirror.atlantic.net/ubuntu xenial-security/universe Sources [38.2 kB]
Get:47 http://mirror.atlantic.net/ubuntu xenial-security/multiverse Sources [1,144 B]
Get:48 http://mirror.atlantic.net/ubuntu xenial-security/main amd64 Packages [345 kB]
Get:49 http://mirror.atlantic.net/ubuntu xenial-security/main i386 Packages [323 kB]
Ign:50 http://mirror.atlantic.net/ubuntu xenial-security/main arm64 Packages
Get:51 http://mirror.atlantic.net/ubuntu xenial-security/main Translation-en [146 kB]
Get:52 http://mirror.atlantic.net/ubuntu xenial-security/restricted amd64 Packages [7,420 B]
Get:53 http://mirror.atlantic.net/ubuntu xenial-security/restricted i386 Packages [7,420 B]
Get:54 http://mirror.atlantic.net/ubuntu xenial-security/restricted Translation-en [2,428 B]
Get:55 http://mirror.atlantic.net/ubuntu xenial-security/universe amd64 Packages [156 kB]
Get:56 http://mirror.atlantic.net/ubuntu xenial-security/universe i386 Packages [137 kB]
Ign:57 http://mirror.atlantic.net/ubuntu xenial-security/universe arm64 Packages
Get:58 http://mirror.atlantic.net/ubuntu xenial-security/universe Translation-en [79.8 kB]
Get:59 http://mirror.atlantic.net/ubuntu xenial-security/multiverse amd64 Packages [2,752 B]
Get:60 http://mirror.atlantic.net/ubuntu xenial-security/multiverse i386 Packages [2,908 B]
Get:61 http://mirror.atlantic.net/ubuntu xenial-security/multiverse Translation-en [1,232 B]
Ign:12 http://mirror.atlantic.net/ubuntu xenial/main arm64 Packages 
Ign:19 http://mirror.atlantic.net/ubuntu xenial/universe arm64 Packages
Ign:23 http://mirror.atlantic.net/ubuntu xenial/multiverse arm64 Packages
Ign:31 http://mirror.atlantic.net/ubuntu xenial-updates/main arm64 Packages
Ign:38 http://mirror.atlantic.net/ubuntu xenial-updates/universe arm64 Packages
Ign:42 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse arm64 Packages
Ign:50 http://mirror.atlantic.net/ubuntu xenial-security/main arm64 Packages
Ign:57 http://mirror.atlantic.net/ubuntu xenial-security/universe arm64 Packages
Ign:12 http://mirror.atlantic.net/ubuntu xenial/main arm64 Packages
Ign:19 http://mirror.atlantic.net/ubuntu xenial/universe arm64 Packages
Ign:23 http://mirror.atlantic.net/ubuntu xenial/multiverse arm64 Packages
Ign:31 http://mirror.atlantic.net/ubuntu xenial-updates/main arm64 Packages
Ign:38 http://mirror.atlantic.net/ubuntu xenial-updates/universe arm64 Packages
Ign:42 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse arm64 Packages
Ign:50 http://mirror.atlantic.net/ubuntu xenial-security/main arm64 Packages
Ign:57 http://mirror.atlantic.net/ubuntu xenial-security/universe arm64 Packages
Err:12 http://mirror.atlantic.net/ubuntu xenial/main arm64 Packages
  404  Not Found [IP: 209.208.0.134 80]
Ign:19 http://mirror.atlantic.net/ubuntu xenial/universe arm64 Packages
Ign:23 http://mirror.atlantic.net/ubuntu xenial/multiverse arm64 Packages
Err:31 http://mirror.atlantic.net/ubuntu xenial-updates/main arm64 Packages
  404  Not Found [IP: 209.208.0.134 80]
Ign:38 http://mirror.atlantic.net/ubuntu xenial-updates/universe arm64 Packages
Ign:42 http://mirror.atlantic.net/ubuntu xenial-updates/multiverse arm64 Packages
Err:50 http://mirror.atlantic.net/ubuntu xenial-security/main arm64 Packages
  404  Not Found [IP: 209.208.0.134 80]
Ign:57 http://mirror.atlantic.net/ubuntu xenial-security/universe arm64 Packages
Fetched 36.5 MB in 6s (6,001 kB/s)                                             
Reading package lists... Done
E: Failed to fetch http://mirror.atlantic.net/ubuntu/dists/xenial/main/binary-arm64/Packages  404  Not Found [IP: 209.208.0.134 80]
E: Failed to fetch http://mirror.atlantic.net/ubuntu/dists/xenial-updates/main/binary-arm64/Packages  404  Not Found [IP: 209.208.0.134 80]
E: Failed to fetch http://mirror.atlantic.net/ubuntu/dists/xenial-security/main/binary-arm64/Packages  404  Not Found [IP: 209.208.0.134 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libllvm3.8
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'git' has no installation candidate
```

Just for FYI

```
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ uname -a
Linux Brigantine 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
```

At a loss on how to fix this. Help greatly appreciated!

---

### Post by oldfred on 2017-08-21
You have three ARM sources, but your system is AMD?

Does not show any arm files, which I do not think you want unless system is Raspberry PI, but then you would not have the amd64 packages.
[URL="http://mirror.atlantic.net/ubuntu/ubuntu/dists/xenial/main/binary-arm64"]http://mirror.atlantic.net/ubuntu/ubuntu/dists/xenial/main/binary-arm64

[http://mirror.atlantic.net/ubuntu/ubuntu/dists/xenial/main/](http://mirror.atlantic.net/ubuntu/ubuntu/dists/xenial/main/)
[/URL]

---

### Post by softwaregoddess2 on 2017-08-21
No, my system is based on a Intel I7(64 bit). The Jetson  Development board has a Arm processor on it.  The ARM sources showed up with installation of the JetPack tools. I am using the i7 machine as the host for Jetson board(connects via Ethernet and serial.) I am not sure why or how the arm packages are being include in the apt-get. Like you I think the arm sources are a clue

---

### Post by softwaregoddess2 on 2017-08-21
More information:

```
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ dpkg --print-architecture
amd64

softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ dpkg --print-foreign-architectures
i386
arm64
softwaregoddess@Brigantine:~/tmp/sources.list.d.old$ dpkg -l |grep arm64
ii  cpp-aarch64-linux-gnu                       4:5.3.1-1ubuntu1                                        amd64        GNU C preprocessor (cpp) for the arm64 architecture
ii  cuda-cublas-cross-aarch64-8-0:arm64         8.0.34-1                                                arm64        CUBLAS cross-aarch64 dev links, headers
ii  cuda-cudart-cross-aarch64-8-0:arm64         8.0.34-1                                                arm64        CUDA Runtime cross-aarch64 dev links, headers
ii  cuda-cufft-cross-aarch64-8-0:arm64          8.0.34-1                                                arm64        CUFFT cross-aarch64 dev links, headers
ii  cuda-curand-cross-aarch64-8-0:arm64         8.0.34-1                                                arm64        CURAND cross-aarch64 dev links, headers
ii  cuda-cusolver-cross-aarch64-8-0:arm64       8.0.34-1                                                arm64        CUSOLVER cross-aarch64 dev links, headers
ii  cuda-cusparse-cross-aarch64-8-0:arm64       8.0.34-1                                                arm64        CUSPARSE cross-aarch64 dev links, headers
ii  cuda-driver-cross-aarch64-8-0:arm64         8.0.34-1                                                arm64        CUDA Driver cross-aarch64 dev links, headers
ii  cuda-misc-headers-cross-aarch64-8-0:arm64   8.0.34-1                                                arm64        CUDA headers for cross-aarch64
ii  cuda-npp-cross-aarch64-8-0:arm64            8.0.34-1                                                arm64        NPP cross-aarch64 dev links, headers
ii  cuda-nvgraph-cross-aarch64-8-0:arm64        8.0.34-1                                                arm64        NVGRAPH cross-aarch64 dev links, headers
ii  cuda-nvml-cross-aarch64-8-0:arm64           8.0.34-1                                                arm64        NVML cross-aarch64 dev links, headers
ii  cuda-nvrtc-cross-aarch64-8-0:arm64          8.0.34-1                                                arm64        NVRTC cross-aarch64 dev links, headers
ii  g++-aarch64-linux-gnu                       4:5.3.1-1ubuntu1                                        amd64        GNU C++ compiler for the arm64 architecture
ii  gcc-aarch64-linux-gnu                       4:5.3.1-1ubuntu1                                        amd64        GNU C compiler for the arm64 architecture
ii  libasan2-arm64-cross                        5.4.0-6ubuntu1~16.04.4cross1                            all          AddressSanitizer -- a fast memory error detector
ii  libatomic1-arm64-cross                      5.4.0-6ubuntu1~16.04.4cross1                            all          support library providing __atomic built-in functions
ii  libc6-arm64-cross                           2.23-0ubuntu3cross1                                     all          GNU C Library: Shared libraries (for cross-compiling)
ii  libc6-dev-arm64-cross                       2.23-0ubuntu3cross1                                     all          GNU C Library: Development Libraries and Header Files (for cross-compiling)
ii  libgcc-5-dev-arm64-cross                    5.4.0-6ubuntu1~16.04.4cross1                            all          GCC support library (development files)
ii  libgcc1-arm64-cross                         1:5.4.0-6ubuntu1~16.04.4cross1                          all          GCC support library
ii  libgomp1-arm64-cross                        5.4.0-6ubuntu1~16.04.4cross1                            all          GCC OpenMP (GOMP) support library
ii  libitm1-arm64-cross                         5.4.0-6ubuntu1~16.04.4cross1                            all          GNU Transactional Memory Library
ii  libstdc++-5-dev-arm64-cross                 5.4.0-6ubuntu1~16.04.4cross1                            all          GNU Standard C++ Library v3 (development files)
ii  libstdc++6-arm64-cross                      5.4.0-6ubuntu1~16.04.4cross1                            all          GNU Standard C++ Library v3
ii  libubsan0-arm64-cross                       5.4.0-6ubuntu1~16.04.4cross1                            all          UBSan -- undefined behaviour sanitizer (runtime)
ii  linux-libc-dev-arm64-cross                  4.4.0-18.34cross1                                       all          Linux Kernel Headers for development (for cross-compiling)
```

---

### Post by softwaregoddess2 on 2017-08-21
Here is something else strange: I would expected /var/lib/apt/lists/ to be larger.

```
softwaregoddess@Brigantine:/var/lib/apt/lists$ ls -al
total 500
drwxr-xr-x 3 root root  20480 Aug 21 10:06 .
drwxr-xr-x 6 root root   4096 Aug 21 10:55 ..
-rw-r--r-- 1 root root  11491 Aug 10 14:41 archive.canonical.com_ubuntu_dists_xenial_InRelease
-rw-r--r-- 1 root root   9534 Aug 10 14:41 archive.canonical.com_ubuntu_dists_xenial_partner_binary-amd64_Packages
-rw-r--r-- 1 root root    698 Aug 10 14:41 archive.canonical.com_ubuntu_dists_xenial_partner_binary-arm64_Packages
-rw-r--r-- 1 root root   9513 Aug 10 14:41 archive.canonical.com_ubuntu_dists_xenial_partner_binary-i386_Packages
-rw-r--r-- 1 root root   4228 Jun 30 18:49 archive.canonical.com_ubuntu_dists_xenial_partner_i18n_Translation-en
-rw-r--r-- 1 root root   6611 Aug 10 14:41 archive.canonical.com_ubuntu_dists_xenial_partner_source_Sources
-rw-r----- 1 root root      0 Aug 18 18:15 lock
drwx------ 2 _apt root  20480 Aug 21 12:17 partial
-rw-r--r-- 1 root root  23829 Aug 14 11:29 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_InRelease
-rw-r--r-- 1 root root  93908 Aug 14 11:14 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_main_binary-amd64_Packages
-rw-r--r-- 1 root root  88166 Aug 14 10:52 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_main_binary-arm64_Packages
-rw-r--r-- 1 root root  93869 Aug 14 11:29 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_main_binary-i386_Packages
-rw-r--r-- 1 root root 103279 Jul 31 13:04 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_main_i18n_Translation-en
softwaregoddess@Brigantine:/var/lib/apt/lists$ cd /var/cache/apt
softwaregoddess@Brigantine:/var/cache/apt$ ls -al
total 2924
drwxr-xr-x  3 root root    4096 Aug 21 12:17 .
drwxr-xr-x 18 root root    4096 Jan 12  2017 ..
drwxr-xr-x  3 root root  180224 Aug 21 11:00 archives
-rw-r--r--  1 root root 2090543 Aug 21 12:17 pkgcache.bin
-rw-r--r--  1 root root  705602 Aug 21 12:17 srcpkgcache.bin
softwaregoddess@Brigantine:/var/cache/apt$ cd archives
softwaregoddess@Brigantine:/var/cache/apt/archives$ ls
lock  partial

```

---

### Post by oldfred on 2017-08-21
Your arm install must assume all sources have the arm appliations.
But the mirror you are using does not.
It may need a different mirror or default Ubuntu or whatever their instructions say to use.

but these do not exist when you go to their site.
```
 archive.canonical.com_ubuntu_dists_xenial_partner_binary-arm64_Packages
ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_xenial_main_binary-arm64_Packages 


```

---

### Post by softwaregoddess2 on 2017-08-24
I need to cross compile, so I need both the amd64,i386 and the arm64 packages.
Verified by the command "dpkg --print-architechture' and "dpkg--print foreigen-archiectures".

I found a repository for the arm64 at "http://ports/ubuntu.com/ubuntu-ports"
I had to duplicate all the current lines in my sources.list and add architecture tags.

For example:

deb [arch=amd64,i386] [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial...
deb [arch=arm64] [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial...

Thanks for your help!

---

