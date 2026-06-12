---
title: "I need help to install DeVeDe"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by moricgaut on 2006-12-27
I have looked on the repositories with synaptic package manager. I have all the repositories clicked on and i also have that universal, multiversal, non-free clicked on all the binary ones. everything is clicked. Yet I can't seem to find it. I'm using ubuntu 6.06. I also found the DeVeDe software on the internet in the file .deb. I clicked on it but i couldn't install it because some depencies were missing. I tried look for the dependentcies but I can't find them on synaptic package manager. Also when I look for them on the internet i find only them in .bzz or whatever file and i don't want to install them that way. So if anybody can help me so that somehow i can get the DeVeDe program working on my computer. Help Me!!!! I need some help or way so that I can install this program on my ubuntu Comp. Thans!

---

### Post by taurus on 2006-12-27
Why don't you post your /etc/apt/sources.list here then?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by moricgaut on 2006-12-27
matthew@matthew-desktop:~$ cat /etc/apt/sources.list

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#AUTOMATIX REPOS END
deb [http://mirrors.kernel.org/debian/](http://mirrors.kernel.org/debian/)

matthew@matthew-desktop:~$

---

### Post by taurus on 2006-12-27
How about

```
sudo aptitude update
sudo aptitude install devede
```

---

### Post by moricgaut on 2006-12-27
matthew@matthew-desktop:~$ sudo aptitude update
Password:
E: Malformed line 50 in source list /etc/apt/sources.list (dist)
E: Malformed line 50 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
matthew@matthew-desktop:~$

it gives me this maybe some wrong with my repositories. Is there way to reset the repositories and put it to the way i got it.

---

### Post by taurus on 2006-12-27
I suppose line 50 is this one here, "deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./"!  Therefore, edit your /etc/apt/sources.list and put a # in front of it...

```
gksudo gedit /etc/apt/sources.list
```
Save the change and run those three commands from above again.

---

### Post by moricgaut on 2006-12-27
well i fixed the problem in the repositorie.

well i did what you said and this what i get. 

matthew@matthew-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Fetched 9B in 14s (1B/s)
Reading package lists... Done
matthew@matthew-desktop:~$ sudo aptitude install devede
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "devede"
The following packages have been kept back:
  amarok amarok-xine amule amule-common bind9-host clamav clamav-base
  clamav-daemon clamav-freshclam clamav-milter cpio dnsutils dpkg dselect
  evince firefox firefox-gnome-support gaim gaim-data gdb gdm gnomebaker
  gnupg gzip hal hal-device-manager info k3b kget knetworkmanager kopete
  ktorrent language-pack-en language-pack-gnome-en libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libavahi-qt3-1
  libbind9-0 libclamav1 libdns21 libgnutls12 libgsf-1-113 libgsf-1-common
  libhal-storage1 libhal1 libimlib2 libisc11 libisccc0 libisccfg1 libk3b2
  liblircclient0 liblwres9 libmagick9 libmilter0 libmusicbrainz4c2a
  libmysqlclient15off libnspr4 libnss3 libpng12-0 libpng12-dev libpq4
  libqt3-mt librpm4 libssl-dev libssl0.9.7 libssl0.9.8 libtag1c2a libtagc0
  libtheora0 libtunepimp-bin libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-image-386 linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386 linux-restricted-modules-common lvm2
  mozilla-thunderbird mysql-common openssh-client openssl python2.4
  python2.4-examples python2.4-gdbm python2.4-minimal python2.4-tk
  readahead rpm screen ssh-askpass-gnome tar xchat xchat-common xinit
0 packages upgraded, 0 newly installed, 0 to remove and 97 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
matthew@matthew-desktop:~$

---

### Post by taurus on 2006-12-27
Hmm...  I remember seeing it in synaptic when I was using Dapper.  Perhaps the Edgy version still works in Dapper.  So, download it from here.

[http://ftp.cs.umn.edu/pub/ubuntu/pool/multiverse/d/devede/devede_2.1-0ubuntu1_all.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/multiverse/d/devede/devede_2.1-0ubuntu1_all.deb)

Then, install it with

```
cd ~/Desktop
sudo dpkg -i devede_2.1-0ubuntu1_all.deb
```
There should be an icon in Applications -> Sound & Video...

---

### Post by moricgaut on 2006-12-27
i can't download it from that url.

---

### Post by moricgaut on 2006-12-27
it's ok i found the file on on [www.getdeb.net](www.getdeb.net) and it installing it right now. thanks for your help. also maybe you can help me with something else. do you know a program on linux so that i can backup my software that i get from synaptic package manager. thanks.

---

