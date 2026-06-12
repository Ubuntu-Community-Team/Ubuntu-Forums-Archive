---
title: "Expert advice needed in Hardy installation [dealing repositories on local hard drive]"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by slax on 2008-05-10
hi guys,

i am using gutsy right now.

me and my friend always install/upgrade Ubuntu using the local repository [which we download from internet]. we installed gutsy with the local repository.

here are my 2 files sources.list & mirror.list

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb file:///var/spool/grepo/ gutsy main restricted universe multiverse
deb file:///var/spool/grepo/ gutsy-updates main restricted universe multiverse
deb file:///var/spool/grepo/ gutsy-backports main restricted universe multiverse
deb file:///var/spool/grepo/ gutsy-security main restricted universe multiverse

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator


```

mirror.list
```

############# config ##################
#
set base_path    /media/F-Drive-SATA320/Repository-gutsy
#
# if you change the base path you must create the directories below with write privlages
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript  $var_path/clean.sh
set defaultarch  i386
set nthreads     20
set tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu

skip-clean http://archive.ubuntu.com/ubuntu/dists/gutsy/main/debian-installer/
skip-clean http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/debian-installer/
skip-clean http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/debian-installer/
skip-clean http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/debian-installer/

```

once i made the changes in these files i used these command in terminal

> /etc/init.d/gdm stop
> apt-get dist-upgrade

Right now i have 2 repositories [gutsy (21.6GB) & hardy (20.5GB)] on my hard drive and i want to install hardy.

i am a bit confused about few things.

1. Should i add the hardy repository along with the gutsy in the mirror.list/sources.list ? as i have to run 'apt-get dist-upgrade'. i need help in adding the right commands in these files.

2. will my drivers get effected by this upgrade ? do i have to install them again ? can i backup my drivers by any means?

3. will the grub get effected by this upgrade [since i am using a 3rd party boot loader, i have to take care of too many things]


- slax

---

