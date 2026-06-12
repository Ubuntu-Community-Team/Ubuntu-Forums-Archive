---
title: "Ubuntu 16.04 local mirror cannot be used to install packages"
date: 2017-03-30
forum: Installation &amp; Upgrades
---

### Post by james-kay on 2017-03-30
I have a mirror which runs on 16.04. It's up to date (apt-mirror) and I have ...


```
root@netboot:/etc/apt# more mirror.list
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the director below with write privileges
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     4
set _tilde 0
#
############# end config ##############


# Xenial 64Bit Mirror - March 2017
deb-amd64 http://archive.ubuntu.com/ubuntu xenial main main/debian-installer restricted restricted/debian-installer universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
clean http://archive.ubuntu.com/ubuntu



```

apt-mirror runs as you would expect:


```
root@netboot:/etc/apt# apt-mirror
Downloading 206 index files using 4 threads...
Begin time: Thu Mar 30 19:58:18 2017
[4]... [3]... [2]... [1]... [0]...
End time: Thu Mar 30 19:58:20 2017


Processing tranlation indexes: [TTTTT]


Downloading 1116 translation files using 4 threads...
Begin time: Thu Mar 30 19:58:20 2017
[4]... [3]... [2]... [1]... [0]...
End time: Thu Mar 30 20:01:16 2017


Processing DEP-11 indexes: [DDDDD]


Downloading 50 dep11 files using 4 threads...
Begin time: Thu Mar 30 20:01:16 2017
[4]... [3]... [2]... [1]... [0]...
End time: Thu Mar 30 20:01:18 2017


Processing indexes: [PPPPP]


0 bytes will be downloaded into archive.
Downloading 0 archive files using 0 threads...
Begin time: Thu Mar 30 20:01:21 2017
[0]...
End time: Thu Mar 30 20:01:21 2017


60.0 MiB in 96 files and 0 directories can be freed.
Run /var/spool/apt-mirror/var/clean.sh for this purpose.


Running the Post Mirror script ...
(/var/spool/apt-mirror/var/postmirror.sh)


/bin/sh: 0: Can't open /var/spool/apt-mirror/var/postmirror.sh


Post Mirror script has completed. See above output for any possible errors.


```


The can't open postmirror problem appears to be a known problem: [https://answers.launchpad.net/ubuntu/+source/apt-mirror/+question/271255](https://answers.launchpad.net/ubuntu/+source/apt-mirror/+question/271255)


The mirror is complete as far as I can tell:


```
user@netboot:/etc/apt$ ls -l /var/www/ubuntu
lrwxrwxrwx 1 root root 54 Mar 30 19:12 /var/www/ubuntu -> /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu
user@netboot:/etc/apt$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         470M     0  470M   0% /dev
tmpfs                         98M  9.5M   89M  10% /run
/dev/mapper/vg_main-lv_root  112G   98G  9.4G  92% /
tmpfs                        488M     0  488M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        488M     0  488M   0% /sys/fs/cgroup
tmpfs                         98M     0   98M   0% /run/user/1000
user@netboot:/etc/apt$ du -sh /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu
96G    /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu
user@netboot:/etc/apt$ ls /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu
dists  pool
user@netboot:/etc/apt$ ls /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/*
/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists:
xenial  xenial-backports  xenial-proposed  xenial-security  xenial-updates


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/pool:
main  multiverse  restricted  universe
user@netboot:/etc/apt$ ls /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/*/*
/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/xenial:
Contents-amd64.gz  InRelease  main  multiverse  Release  Release.gpg  restricted  universe


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/xenial-backports:
Contents-amd64.gz  InRelease  main  multiverse  Release  Release.gpg  restricted  universe


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/xenial-proposed:
Contents-amd64.gz  InRelease  main  multiverse  Release  Release.gpg  restricted  universe


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security:
Contents-amd64.gz  InRelease  main  multiverse  Release  Release.gpg  restricted  universe


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/xenial-updates:
Contents-amd64.gz  InRelease  main  multiverse  Release  Release.gpg  restricted  universe


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/pool/main:
a  c  e  g  i  k  liba  libc  libe  libg  libi  libk  libm  libo  libq  libs  libu  libw  liby  m  o  q  s  u  w  y
b  d  f  h  j  l  libb  libd  libf  libh  libj  libl  libn  libp  libr  libt  libv  libx  libz  n  p  r  t  v  x  z


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/pool/multiverse:
3  a  b  c  d  e  f  g  h  i  j  k  l  liba  libc  libd  libf  libg  libm  libs  libt  libv  liby  m  n  o  p  q  r  s  t  u  v  w  x  y  z


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/pool/restricted:
b  i  n


/var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/pool/universe:
0  3  6  9  b  d  f  h  j  l     liba  libc  libe  libg  libi  libk  libm  libo  libq  libs  libu  libw  liby  m  o  q  s  u  w  y
2  4  7  a  c  e  g  i  k  lib3  libb  libd  libf  libh  libj  libl  libn  libp  libr  libt  libv  libx  libz  n  p  r  t  v  x  z
user@netboot:/etc/apt$


```


Now set /etc/apt/sources like this:

```
root@netboot:~# cat /etc/apt/sources.list
deb [http://netboot.domain.com/ubuntu/](http://netboot.domain.com/ubuntu/) xenial main restricted universe multiverse
deb [http://netboot.domain.com/ubuntu/](http://netboot.domain.com/ubuntu/) xenial-updates main restricted universe multiverse
deb [http://netboot.domain.com/ubuntu/](http://netboot.domain.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://netboot.domain.com/ubuntu/](http://netboot.domain.com/ubuntu/) xenial-security main restricted universe multiverse


root@netboot:~# apt-get update
Get:2 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports InRelease [102 kB]
Get:4 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security InRelease [102 kB]
Get:1 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial InRelease [247 kB]
Ign:5 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main amd64 Packages
Ign:6 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main i386 Packages
Ign:7 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main Translation-en
Ign:8 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted amd64 Packages
Ign:9 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted i386 Packages
Ign:10 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted Translation-en
Ign:11 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe amd64 Packages
Ign:12 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe i386 Packages
Ign:13 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe Translation-en
Ign:14 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse amd64 Packages
Ign:15 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse i386 Packages
Ign:16 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse Translation-en
Get:5 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main amd64 Packages [501 kB]
Ign:6 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main i386 Packages
Get:7 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main Translation-en [202 kB]
Get:8 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted amd64 Packages [7,776 B]
Ign:9 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted i386 Packages
Get:10 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted Translation-en [2,548 B]
Get:11 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe amd64 Packages [450 kB]
Ign:12 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe i386 Packages
Get:13 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe Translation-en [172 kB]
Get:14 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse amd64 Packages [8,920 B]
Ign:15 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse i386 Packages
Get:16 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse Translation-en [4,136 B]
Ign:6 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main i386 Packages
Ign:9 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted i386 Packages
Ign:12 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe i386 Packages
Ign:15 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse i386 Packages
Err:6 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/main i386 Packages
  404  Not Found
Ign:9 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/restricted i386 Packages
Ign:12 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/universe i386 Packages
Ign:15 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-updates/multiverse i386 Packages
Ign:17 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main amd64 Packages
Ign:18 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main i386 Packages
Ign:19 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main Translation-en
Ign:20 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe amd64 Packages
Ign:21 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe i386 Packages
Ign:22 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe Translation-en
Get:17 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main amd64 Packages [4,672 B]
Ign:18 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main i386 Packages
Get:19 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main Translation-en [3,200 B]
Get:20 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe amd64 Packages [2,512 B]
Ign:21 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe i386 Packages
Get:22 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe Translation-en [1,216 B]
Ign:18 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main i386 Packages
Ign:21 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe i386 Packages
Err:18 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/main i386 Packages
  404  Not Found
Ign:21 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-backports/universe i386 Packages
Ign:23 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main amd64 Packages
Ign:24 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main i386 Packages
Ign:25 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main Translation-en
Ign:26 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted amd64 Packages
Ign:27 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted i386 Packages
Ign:28 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted Translation-en
Ign:29 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe amd64 Packages
Ign:30 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe i386 Packages
Ign:31 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe Translation-en
Ign:32 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse amd64 Packages
Ign:33 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse i386 Packages
Ign:34 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse Translation-en
Get:23 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main amd64 Packages [235 kB]
Ign:24 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main i386 Packages
Get:25 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main Translation-en [99.7 kB]
Get:26 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted amd64 Packages [7,428 B]
Ign:27 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted i386 Packages
Get:28 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted Translation-en [2,428 B]
Get:29 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe amd64 Packages [105 kB]
Ign:30 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe i386 Packages
Get:31 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe Translation-en [54.4 kB]
Get:32 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse amd64 Packages [2,748 B]
Ign:33 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse i386 Packages
Get:34 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse Translation-en [1,232 B]
Ign:24 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main i386 Packages
Ign:27 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted i386 Packages
Ign:30 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe i386 Packages
Ign:33 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse i386 Packages
Err:24 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/main i386 Packages
  404  Not Found
Ign:27 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/restricted i386 Packages
Ign:30 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/universe i386 Packages
Ign:33 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial-security/multiverse i386 Packages
Ign:35 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main amd64 Packages
Ign:36 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main i386 Packages
Ign:37 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main Translation-en_GB
Ign:38 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main Translation-en
Ign:39 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted amd64 Packages
Ign:40 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted i386 Packages
Ign:41 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted Translation-en_GB
Ign:42 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted Translation-en
Ign:43 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe amd64 Packages
Ign:44 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe i386 Packages
Ign:45 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe Translation-en_GB
Ign:46 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe Translation-en
Ign:47 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse amd64 Packages
Ign:48 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse i386 Packages
Ign:49 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse Translation-en_GB
Ign:50 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse Translation-en
Get:35 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main amd64 Packages [1,201 kB]
Ign:36 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main i386 Packages
Get:37 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main Translation-en_GB [426 kB]
Get:38 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main Translation-en [568 kB]
Get:39 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted amd64 Packages [8,344 B]
Ign:40 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted i386 Packages
Get:41 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted Translation-en_GB [2,556 B]
Get:42 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted Translation-en [2,908 B]
Get:43 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe amd64 Packages [7,532 kB]
Ign:44 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe i386 Packages
Get:45 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe Translation-en_GB [3,040 kB]
Get:46 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe Translation-en [4,354 kB]
Get:47 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse amd64 Packages [144 kB]
Ign:48 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse i386 Packages
Get:49 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse Translation-en_GB [88.1 kB]
Get:50 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse Translation-en [106 kB]
Ign:36 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main i386 Packages
Ign:40 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted i386 Packages
Ign:44 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe i386 Packages
Ign:48 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse i386 Packages
Err:36 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/main i386 Packages
  404  Not Found
Ign:40 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/restricted i386 Packages
Ign:44 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/universe i386 Packages
Ign:48 [http://netboot.domain.com/ubuntu](http://netboot.domain.com/ubuntu) xenial/multiverse i386 Packages
Fetched 2,421 kB in 1s (1,619 kB/s)
Reading package lists... Done
E: Failed to fetch [http://netboot.domain.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages](http://netboot.domain.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://netboot.domain.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages](http://netboot.domain.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://netboot.domain.com/ubuntu/dists/xenial-security/main/binary-i386/Packages](http://netboot.domain.com/ubuntu/dists/xenial-security/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://netboot.domain.com/ubuntu/dists/xenial/main/binary-i386/Packages](http://netboot.domain.com/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.


```


And try to install something.... bc for example:
```

root@netboot:~# apt-get install bc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package bc
root@netboot:~#

```

It should be there...  [http://packages.ubuntu.com/xenial/bc](http://packages.ubuntu.com/xenial/bc)   and the files are present.


```
root@netboot:~# ls -ld /var/www/ubuntu/pool/main/b/bc
drwxr-xr-x 2 root root 4096 Mar 30 13:23 /var/www/ubuntu/pool/main/b/bc
root@netboot:~# ls -l /var/www/ubuntu/pool/main/b/bc
total 132
-rw-r--r-- 1 root root 82552 Dec 11  2014 bc_1.06.95-9build1_amd64.deb
-rw-r--r-- 1 root root 46386 Dec 11  2014 dc_1.06.95-9build1_amd64.deb
```

Any ideas?

---

