---
title: "error upgrading newest software updates in gutsy"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by sporto on 2007-11-15
hi all, can anyone help me with the following?

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Segmentation fault (core dumped)
Setting up libpango1.0-common (1.18.3-0ubuntu1) ...
Segmentation fault (core dumped)
dpkg: error processing libpango1.0-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.18.3-0ubuntu1); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpoppler-glib2:
 libpoppler-glib2 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpoppler-glib2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
 evince depends on libpoppler-glib2 (>= 0.6); however:
  Package libpoppler-glib2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.14-19 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.16.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
 gtkhtml3.14 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtksourceview2.0-0:
 libgtksourceview2.0-0 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtksourceview2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwnck22:
 libwnck22 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libwnck22 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx-new:
 nvidia-glx-new depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing nvidia-glx-new (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sound-juicer:
 sound-juicer depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 sound-juicer depends on libpango1.0-0 (>= 1.18.3); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing sound-juicer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpango1.0-common
 libpango1.0-0
 libgnomeui-0
 eog
 libpoppler-glib2
 evince
 file-roller
 libgtkhtml3.14-19
 gtkhtml3.14
 libgtksourceview2.0-0
 libwnck22
 nvidia-glx-new
 sound-juicer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by taurus on 2007-11-15
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by sporto on 2007-11-15
Here is the sources.list, thanks for your help.

```

cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate amd64 (20071009.1)]/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy restricted main #Added by software-properties
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate amd64 (20071009.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
```

---

### Post by taurus on 2007-11-15
Is it a fresh install or did you upgrade from Feisty to Gutsy?  What happens if you run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sporto on 2007-11-15
it's a fresh install, i've been running it fine for the past few weeks...
I was earlier today getting an error about gb.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-amd64_Packages when running apt-get update so I moved the file from  /var/lib/apt/lists/ to my home dir and updated apt again. I assume it fetched this file.. it didn't error but did when doing upgrade in the same way it does now. I've tried moving the file back to no avail. I now have a bunch of packages that are downloaded but not configured but won't configure because they all depend on libpango which won't configure..
```

@ubuntu:~$ sudo apt-get update
Get: 1 http://gb.archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://gb.archive.ubuntu.com gutsy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/multiverse Translation-en_GB
Get: 2 http://gb.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com gutsy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB
Get: 3 http://gb.archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://gb.archive.ubuntu.com gutsy-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy Release
Hit http://gb.archive.ubuntu.com gutsy-updates Release
Hit http://gb.archive.ubuntu.com gutsy-security Release
Hit http://gb.archive.ubuntu.com gutsy/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy/main Sources
Hit http://gb.archive.ubuntu.com gutsy/main Packages
Hit http://gb.archive.ubuntu.com gutsy/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy/multiverse Sources
Hit http://gb.archive.ubuntu.com gutsy/universe Sources
Hit http://gb.archive.ubuntu.com gutsy/universe Packages
Hit http://gb.archive.ubuntu.com gutsy/multiverse Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/main Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/main Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com gutsy-security/main Packages
Hit http://gb.archive.ubuntu.com gutsy-security/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy-security/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy-security/main Sources
Hit http://gb.archive.ubuntu.com gutsy-security/multiverse Sources
Hit http://gb.archive.ubuntu.com gutsy-security/universe Sources
Hit http://gb.archive.ubuntu.com gutsy-security/universe Packages
Hit http://gb.archive.ubuntu.com gutsy-security/multiverse Packages
Fetched 3B in 0s (17B/s)
Reading package lists... Done
@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Segmentation fault (core dumped)
Setting up libpango1.0-common (1.18.3-0ubuntu1) ...
Segmentation fault (core dumped)
dpkg: error processing libpango1.0-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.18.3-0ubuntu1); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpoppler-glib2:
 libpoppler-glib2 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpoppler-glib2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
 evince depends on libpoppler-glib2 (>= 0.6); however:
  Package libpoppler-glib2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.14-19 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.16.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
 gtkhtml3.14 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtksourceview2.0-0:
 libgtksourceview2.0-0 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtksourceview2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwnck22:
 libwnck22 depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libwnck22 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx-new:
 nvidia-glx-new depends on libpango1.0-0 (>= 1.18.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing nvidia-glx-new (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sound-juicer:
 sound-juicer depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 sound-juicer depends on libpango1.0-0 (>= 1.18.3); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing sound-juicer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpango1.0-common
 libpango1.0-0
 libgnomeui-0
 eog
 libpoppler-glib2
 evince
 file-roller
 libgtkhtml3.14-19
 gtkhtml3.14
 libgtksourceview2.0-0
 libwnck22
 nvidia-glx-new
 sound-juicer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sporto on 2007-11-15
so I rebooted the machine and ran apt-get upgrade again and it worked fine...

very odd?

---

