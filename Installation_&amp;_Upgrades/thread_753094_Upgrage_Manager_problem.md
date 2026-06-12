---
title: "Upgrage Manager problem"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by rjrowe on 2008-04-12
I copied some files from an older computer to this one and now my Upgrade Manager fails. I get this message for every file I wish to update:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.2p1-7ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.2p1-7ubuntu3.3_i386.deb)
  400 Bad Request

The older computer is using ver 5.10 Breezy Badger and this one is using 6.06 LTS - Dapper Drake.

I suspect that I overwrote a configuration file, but what one (if it IS the problem) and how do I fix it?

rjrowe

---

### Post by PmDematagoda on 2008-04-12
Post the output of:-
```
sudo apt-get update
```

---

### Post by Pumalite on 2008-04-12
Post:
cat /etc/apt/sources.list

---

### Post by rjrowe on 2008-04-12
> **PmDematagoda said:**
> Post the output of:-
```
sudo apt-get update
```

output follows:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  400 Bad Request
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  400 Bad Request
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  400 Bad Request
Reading package lists...

rjrowe

---

### Post by rjrowe on 2008-04-12
> **Pumalite said:**
> Post:
cat /etc/apt/sources.list

this is the text:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

rjrowe

---

### Post by Pumalite on 2008-04-12
Check your connection and/or change Server.

---

### Post by rjrowe on 2008-04-13
> **Pumalite said:**
> Check your connection and/or change Server.

Please excuse my ignorance, but give me an example of a different server.

rjrowe

---

### Post by Pumalite on 2008-04-13
System>Administration>Software Sources Go from USA to 'Main? as an examle.

---

### Post by rjrowe on 2008-04-14
> **Pumalite said:**
> System>Administration>Software Sources Go from USA to 'Main? as an examle.

It looks to me that all the pertainant ones are already Main. I tried changing one or more and got the following:

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 400 Bad Request
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 400 Bad Request
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 400 Bad Request
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 400 Bad Request
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 400 Bad Request

It is getting to be an old refrain!

rjrowe

---

### Post by rjrowe on 2008-04-14
> **Pumalite said:**
> System>Administration>Software Sources Go from USA to 'Main? as an examle.

Oh, one more thing - When I closed my Internet connection a box popped up with the following message:

duplicate sources.list entry: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/ver/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

I looked at /var/lib/apt/lists and could find no duplicates, certainly not the one described. Nor could I find any duplicate listings in /etc/apt/sources.list  Am I misunderstanding the error message?

rjrowe

---

### Post by Pumalite on 2008-04-14
Post:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudp apt-get upgrade

---

### Post by rjrowe on 2008-04-16
> **Pumalite said:**
> Post:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudp apt-get upgrade

dpkg --configure -a gives me nothing, just the prompt again.

apt-get -f install gives:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

apt-get update gives:
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  400 Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  400 Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  400 Bad Request
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  400 Bad Request
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  400 Bad Request
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  400 Bad Request
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

apt-get upgrade gives:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  cupsys cupsys-bsd cupsys-client gs-esp libcupsimage2 libcupsys2 libmysqlclient15off mysql-common openssh-client
  openssh-server ssh ssh-askpass-gnome
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7698kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Y
WARNING: The following packages cannot be authenticated!
  openssh-server openssh-client libcupsys2 libcupsimage2 gs-esp cupsys cupsys-bsd cupsys-client mysql-common
  libmysqlclient15off ssh ssh-askpass-gnome
Install these packages without verification [y/N]?
y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main openssh-server 1:4.2p1-7ubuntu3.3
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssh-server 1:4.2p1-7ubuntu3.3
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssh-client 1:4.2p1-7ubuntu3.3
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libcupsys2 1.2.2-0ubuntu0.6.06.8
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libcupsimage2 1.2.2-0ubuntu0.6.06.8
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gs-esp 8.15.2.dfsg.0ubuntu1-0ubuntu1.1
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main cupsys 1.2.2-0ubuntu0.6.06.8
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main cupsys-bsd 1.2.2-0ubuntu0.6.06.8
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main cupsys-client 1.2.2-0ubuntu0.6.06.8
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main mysql-common 5.0.22-0ubuntu6.06.9
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libmysqlclient15off 5.0.22-0ubuntu6.06.9
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main ssh 1:4.2p1-7ubuntu3.3
  400 Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main ssh-askpass-gnome 1:4.2p1-7ubuntu3.3
  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.2p1-7ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.2p1-7ubuntu3.3_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.2p1-7ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.2p1-7ubuntu3.3_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.2-0ubuntu0.6.06.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.2-0ubuntu0.6.06.8_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.2-0ubuntu0.6.06.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.2-0ubuntu0.6.06.8_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gs-esp/gs-esp_8.15.2.dfsg.0ubuntu1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gs-esp/gs-esp_8.15.2.dfsg.0ubuntu1-0ubuntu1.1_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.2-0ubuntu0.6.06.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.2-0ubuntu0.6.06.8_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.2-0ubuntu0.6.06.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.2-0ubuntu0.6.06.8_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.2-0ubuntu0.6.06.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.2-0ubuntu0.6.06.8_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06.9_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06.9_all.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06.9_i386.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.2p1-7ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.2p1-7ubuntu3.3_all.deb)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.2p1-7ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.2p1-7ubuntu3.3_i386.deb)  400 Bad Request
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


rjrowe

---

### Post by Pumalite on 2008-04-16
Bad connection I think. Post:
ip addr

---

### Post by rjrowe on 2008-04-16
> **Pumalite said:**
> Bad connection I think. Post:
ip addr

1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:14:2a:21:a0:8f brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.2/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::214:2aff:fe21:a08f/64 scope link
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

rjrowe

---

### Post by Pumalite on 2008-04-16
You seem to have eth0 up and running. I suggest you get a new sources.list and try. I'd give you mine, but I'm running Hardy. Maybe someone can post theirs.

---

### Post by rjrowe on 2008-04-21
> **Pumalite said:**
> You seem to have eth0 up and running. I suggest you get a new sources.list and try. I'd give you mine, but I'm running Hardy. Maybe someone can post theirs.

I tried that - still no luck! Maybe I'll just wait until Hardy is released and install that.

rjrowe

---

### Post by rjrowe on 2008-05-29
I have updated to Hardy, but I still cannot use the update manager. It responds with the following:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  400 Bad Request
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  400 Bad Request
Some index files failed to download, they have been ignored, or old ones used instead.

Excuse the newbie question - I can add these to a config file, but what file? and where is it?

I discovered /etc/apt/sources.list and added the above lines as per the pattern of other urls. Anything I do seems to only make it worse. Now there are many more lines on the "failed to fetch" message.

Maybe someone could send me their sources.list file?

rj rowe


RJ

---

