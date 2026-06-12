---
title: "apt-mirror pre-seeding with CD .deb contents?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2008-10-30
I will be upgrading servers and desktops from 8.04.1 to 8.10 ASAP. I have installed apt-mirror on each office's LAN server. I would like to copy the .deb and other content from the ISO CD's before turning on the mirror, for bandwidth conservation.

```
$ cat /etc/apt/mirror.list 
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu
```
Obviously the layout has to be exact, can someone tell me specifically what to copy where from the CD/ISO to the filesystem, and permissions, ownership, etc to get the mirror at least partly pre-seeded but still remain a true mirror when done?

Thanks.

---

