---
title: "apt-mirror not able to install from repo"
date: 2018-07-12
forum: Installation &amp; Upgrades
---

### Post by eclay on 2018-07-12
Hello, I've been using apt-mirror to create a local repo of ubuntu 18.04 which seems to work just fine for applying updates/patches to systems already with ubuntu running on them.  When I attempt to perform a network install from a private not publicly routable network it fails once it gets to the "download installer components" step in the install process.  The error message says 'the installer failed to download a file from the mirror.  this may be a problem with your network, or with the mirror.  you can choose to retry the download, select a different mirror, or cancel and choose another installation method.'  If I change the preseed file to point to a different url that contains a copy of the content of the ubuntu server install iso in it the install runs just fine.  My question is should I be able to perform a network install via the apt-mirror repo or not?  Is there a step I'm missing here that is needed to allow for local installs via the apt-mirror local repo.

/etc/apt/mirror.list
```
  # set base_path    /var/spool/apt-mirror#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############


deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse


deb-i386 http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


deb-i386 http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


clean http://archive.ubuntu.com/ubuntu 
```

---

### Post by eclay on 2018-07-17
After looking at this a bit more I've had to manually download to the correct local repo location the following files and still not got them all.

apt-mirror-setup_0.104ubuntu5_all.udeb
apt-setup-udeb_0.104ubuntu5_amd64.udeb
base-installer_1.158ubuntu4_amd64.udeb
block-modules-4.15.0-20-generic-di_4.15.0-20.21_amd64.udeb

I would think there is something I'm missing in my mirror.list that it's failing to download the needed files with out manual intervention.

---

