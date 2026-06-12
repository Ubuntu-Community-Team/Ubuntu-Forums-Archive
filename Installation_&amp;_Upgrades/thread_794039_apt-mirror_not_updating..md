---
title: "apt-mirror not updating."
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by phillhs on 2008-05-14
Hi,

I seem to have a problem getting apt-mirror to update from a network mirror to a local mirror, the contents of my /etc/apt-mirror are :-

```


############# config ##################
#
set base_path    /other/repo
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     10
set tilde 0
#
############# end config ##############

deb http://uk.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

deb-src http://uk.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse

#clean http://archive.ubuntu.com/ubuntu
clean http://uk.archive.ubuntu.com/ubuntu


```

When I run apt-mirror I get :-

```

phill@quinn:~$ sudo apt-mirror
Downloading 95 index files using 10 threads...
Begin time: Wed May 14 15:03:44 2008
[10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Wed May 14 15:03:47 2008

Proceed indexes: [SSSSSPPPPP]

0.0 bytes will be downloaded into archive.
Downloading 0 archive files using 0 threads...
Begin time: Wed May 14 15:03:56 2008
[0]...
End time: Wed May 14 15:03:56 2008

0.0 bytes in 0 files and 0 directories can be freed.
Run /other/repo/var/clean.sh for this purpose.

```

However there is a package that I am trying to update (nfs-common), which is definatly on the site I'm mirroring from at :-

[http://uk.archive.ubuntu.com/ubuntu/pool/main/n/nfs-utils/nfs-common_1.1.2-2ubuntu2.1_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/n/nfs-utils/nfs-common_1.1.2-2ubuntu2.1_i386.deb)

However it never seems to be mirrored to my local repository, which still has the previous version, and so I can't update my system.

What am i doing wrong ?

Cheers.

Phill.

---

