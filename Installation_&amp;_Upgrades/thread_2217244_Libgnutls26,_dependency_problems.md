---
title: "Libgnutls26, dependency problems"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by obdeath on 2014-04-16
Hi all, wondered if anyone could help me. 

Apt-get upgrade is broken, have run apt-get -f install and get the below error

> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgnutls26
Suggested packages:
  gnutls-bin
The following packages will be upgraded:
  libgnutls26
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/459 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.12.14-5ubuntu3.6 cannot be configured because libgnutls26:i386 is in a different version (2.12.14-5ubuntu3.7)
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.12.14-5ubuntu3.7 cannot be configured because libgnutls26:amd64 is in a different version (2.12.14-5ubuntu3.6)
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libcurl3-gnutls:
 libcurl3-gnutls depends on libgnutls26 (>= 2.12.6.1-0); however:
  Package libgnutls26 is not configured yet.
dpkg: error processing libcurl3-gnutls (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vino:
 vino depends on libgnutls26 (>= 2.12.6.1-0); however:
  Package libgnutls26 is not configured yet.
dpkg: error processing vino (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        Errors were encountered while processing:
 libgnutls26
 libgnutls26:i386
 libcurl3-gnutls
 vino



output from sudo dpkg --audit

> sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libcurl3-gnutls      Multi-protocol file transfer library (GnuTLS)
 libgnutls26:i386     GNU TLS library - runtime library
 vino                 VNC server for GNOME

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libgnutls26          GNU TLS library - runtime library

output from sudo dpkg --configure libgnutls26

> sudo dpkg --configure libgnutls26
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.12.14-5ubuntu3.6 cannot be configured because libgnutls26:i386 is in a different version (2.12.14-5ubuntu3.7)
Errors were encountered while processing:
 libgnutls26

any ideas?

cheers for reading

---

### Post by Ubi_one_2014 on 2014-04-16
you mixing 32bits and 64 bits

[COLOR=#000000]*dpkg: error processing libgnutls26 (--configure):*[/COLOR]
[COLOR=#000000]*libgnutls26:amd64 2.12.14-5ubuntu3.6 cannot be configured because libgnutls26:i386 is in a different version (2.12.14-5ubuntu3.7)*[/COLOR]
[COLOR=#000000]*dpkg: error processing libgnutls26:i386 (--configure):*[/COLOR]
[COLOR=#000000]*libgnutls26:i386 2.12.14-5ubuntu3.7 cannot be configured because libgnutls26:amd64 is in a different version (2.12.14-5ubuntu3.6*[/COLOR]

thath will cause seriuos problems


what shows

cat /etc/apt/sources.list

---

### Post by obdeath on 2014-04-16
Cheers Ubi_one_2014. 

> **Ubi_one_2014 said:**
> cat /etc/apt/sources.list
cat /etc/apt/sources.list output 

> cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to natty
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free



---

### Post by mörgæs on 2014-04-16
The system was born as a 10.04 install, which has been upgraded four times to 12.04. 
Now there's a package conflict and if you manage to solve it you are still a long step away from 14.04, which is released tomorrow.

If your can live with the system as it is a little more you could consider to leave it for now and do a fresh install of 14.04 after a week or so.

---

### Post by Ubi_one_2014 on 2014-04-16
i agree

try as a last resort
go to: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

create sources.list for your distro

copy it
logn as root, cd /etc/apt
mv sources.list sources.list.backup
open sources.list. with kate or gedit
remove all lines, and past the copied sources you just created

save

apt-get -f install

what happends?

---

### Post by obdeath on 2014-04-17
thanks a lot, the new sources list fixed it, cheers for all the help

---

### Post by mörgæs on 2014-04-17
Good, please mark the thread 'solved'.

---

### Post by Ubi_one_2014 on 2014-04-17
lovely

---

