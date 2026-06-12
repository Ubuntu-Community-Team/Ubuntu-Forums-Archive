---
title: "HELP!! I can't upgrade to 7.04 (from 6.1) Nvidea problem!?"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by error404 on 2007-12-16
Every time I try to upgrade it says:

> 
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz) Could not resolve 'nvidia.limitless.lupine.me.uk'

 

I know I mess something up bery-l before so I imagine that my problem is related to that :confused:

---

### Post by PmDematagoda on 2007-12-16
Please post the result of:-
```

cat /etc/apt/sources.list
```

---

### Post by error404 on 2007-12-16
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
deb http://ubuntu.beryl-project.org/ edgy main


```

---

### Post by PmDematagoda on 2007-12-16
Open the sources.list file for editing using:- 

```
gksudo gedit /etc/apt/sources.list
```

Then edit the file to look like this:-

The red lines have the # typed in front of them whereas the blue lines have the # removed.
```
[COLOR="Red"]#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted[/COLOR]
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Blue"]deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
[/COLOR]
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

[COLOR="Blue"]deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe [/COLOR]#Added by software-properties
[COLOR="Blue"]deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe[/COLOR]
[COLOR="Red"]#deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
#deb http://ubuntu.beryl-project.org/ edgy main[/COLOR]
```

After you edit the file, save it and do:-

```
sudo apt-get update
```

After that is complete try upgrading Ubuntu again.

---

### Post by error404 on 2007-12-16
thank you... It worked fine!

---

