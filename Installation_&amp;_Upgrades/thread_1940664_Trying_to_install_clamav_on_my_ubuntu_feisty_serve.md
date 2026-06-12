---
title: "Trying to install clamav on my ubuntu feisty server"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by lenkaotap on 2012-03-14
I am trying to install clamav on my server, which runs ubuntu feisty (I should upgrade I know ... will get there someday).

Running sudo apt-get install clamav gives me these errors:

```
Err http://dk.archive.ubuntu.com feisty/main libgmp3c2 2:4.2.1+dfsg-4build1
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe libclamav3 0.92.1~dfsg2-1.1~feisty3.1
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe clamav-base 0.92.1~dfsg2-1.1~feisty3.1
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe clamav-freshclam 0.92.1~dfsg2-1.1~feisty3.1
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe clamav 0.92.1~dfsg2-1.1~feisty3.1
  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-4build1_i386.deb  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/libclamav3_0.92.1~dfsg2-1.1~feisty3.1_i386.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-base_0.92.1~dfsg2-1.1~feisty3.1_all.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-freshclam_0.92.1~dfsg2-1.1~feisty3.1_i386.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav_0.92.1~dfsg2-1.1~feisty3.1_i386.deb  404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I assume it's because it's not longer supported for feisty?

So I tried to find a source ... found one here:
[https://launchpad.net/ubuntu/+source/clamav/0.90-1ubuntu1](https://launchpad.net/ubuntu/+source/clamav/0.90-1ubuntu1) 

But trying to install it gives me following errors:
```
lenka@morsverden:~/clamav-0.90$ sh ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I'm not really updated in my linux installing skills, so any help would be appretiated. Is there any easy way to apt-get install if the links are not working?

---

### Post by raja.genupula on 2012-03-14
change your update manager server to best server .

update manager -> settings -> in the first TAB at Download from . change it to best server and then try again installing from your terminal . 

have you installed **build-essential**  ?

---

### Post by lenkaotap on 2012-03-14
> **raja.genupula said:**
> change your update manager server to best server .

update manager -> settings -> in the first TAB at Download from . change it to best server and then try again installing from your terminal . 

have you installed **build-essential**  ?
I can only acces my server in a terminal ... what should I write in the shell to change it?

I haven't installed anything in a couple of years, so not sure what's on there ...

---

### Post by raja.genupula on 2012-03-14
do this in terminal 
```
sudo apt-get install build-essential
```and try again doing compiling .

---

### Post by lenkaotap on 2012-03-14
> **raja.genupula said:**
> do this in terminal 
```
sudo apt-get install build-essential
```and try again doing compiling .

I get the folowing errors:

```
lenka@morsverden:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 202 not upgraded.
Need to get 8056kB of archives.
After unpacking 33,7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-libc-dev libc6-dev libstdc++6-4.1-dev g++-4.1 g++ dpkg-dev build-essential
Install these packages without verification [y/N]? y
Err http://dk.archive.ubuntu.com feisty-updates/main linux-libc-dev 2.6.20-17.39
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main libc6-dev 2.5-0ubuntu14
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main g++-4.1 4.1.2-0ubuntu4
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main g++ 4:4.1.2-1ubuntu1
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main dpkg-dev 1.13.24ubuntu6
  404 Not Found
Err http://dk.archive.ubuntu.com feisty/main build-essential 11.3
  404 Not Found
Err http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-17.39
  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-17.39_i386.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb  404 Not Found
Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Seems like I always get that with apt-get. Is it because my ubuntu version is to outdated?

---

### Post by raja.genupula on 2012-03-15
yes i think . you better to go for upgrading to latest versions with necessary backup's . 

your versions seems not even LTS . so what i suggest is make a fresh install with recent version  . 

for more information regarding your version look at this 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

