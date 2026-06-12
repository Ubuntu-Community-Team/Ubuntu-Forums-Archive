---
title: "lib32gcc-4.8-dev : Depends: libx32gcc1 (&gt;= 1:4.8.2-19ubuntu1) but it is not going to"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by mattismyname on 2015-03-13
Trying to run an apt-get upgrade on my Trusty system and get the following error. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 lib32gcc-4.7-dev : Depends: libx32gcc1 (>= 1:4.7.3-12ubuntu1) but it is not installed
                    Depends: libx32quadmath0 (>= 4.7.3-12ubuntu1) but it is not installed
 lib32gcc-4.8-dev : Depends: libx32gcc1 (>= 1:4.8.2-19ubuntu1) but it is not installed
                    Depends: libx32quadmath0 (>= 4.8.2-19ubuntu1) but it is not installed
 lib64readline6-dev:i386 : Depends: libc6-dev-amd64:i386 but it is not installed
 libx32asan0 : Depends: libc6-x32 (>= 2.16) but it is not installed
               Depends: libx32gcc1 but it is not installed
 libx32atomic1 : Depends: libc6-x32 (>= 2.16) but it is not installed
 libx32gomp1 : Depends: libc6-x32 (>= 2.17) but it is not installed
 libx32itm1 : Depends: libc6-x32 (>= 2.16) but it is not installed
E: Unmet dependencies. Try using -f.

```

I've tried running 'apt-get -f install' as recommended, but get the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32asan0 lib32atomic1 lib32gomp1 lib32itm1 lib32quadmath0 lib32stdc++6
  lib64asan0:i386 lib64atomic1:i386 lib64gcc-4.8-dev:i386 lib64gcc1:i386
  lib64gomp1:i386 lib64itm1:i386 lib64quadmath0:i386 libasan0:i386
  libatomic1:i386 libc6-dev-x32:i386 libc6-x32:i386 libcloog-isl4:i386
  libgcc-4.8-dev:i386 libgmp10:i386 libgomp1:i386 libisl10:i386 libitm1:i386
  libmpc3:i386 libmpfr4:i386 libquadmath0:i386 libx32asan0:i386
  libx32atomic1:i386 libx32gcc-4.8-dev:i386 libx32gcc1:i386 libx32gomp1:i386
  libx32itm1:i386 libx32quadmath0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev-amd64:i386
Recommended packages:
  gcc-multilib:i386
The following packages will be REMOVED:
  lib32gcc-4.7-dev lib32gcc-4.8-dev lib32stdc++-4.8-dev lib32stdc++6-4.7-dev
  libx32asan0 libx32atomic1 libx32gomp1 libx32itm1
The following NEW packages will be installed:
  libc6-dev-amd64:i386
0 upgraded, 1 newly installed, 8 to remove and 145 not upgraded.
20 not fully installed or removed.
Need to get 0 B/1,429 kB of archives.
After this operation, 10.1 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 529565 files and directories currently installed.)
Preparing to unpack .../libc6-dev-amd64_2.19-0ubuntu6.6_i386.deb ...
Unpacking libc6-dev-amd64 (2.19-0ubuntu6.6) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-amd64_2.19-0ubuntu6.6_i386.deb (--unpack):
 trying to overwrite '/usr/include/gnu', which is also in package libc6-dev-i386 2.19-0ubuntu6.6
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-amd64_2.19-0ubuntu6.6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can any packaging wizards help me understand how to resolve this?

Thanks!

---

