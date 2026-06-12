---
title: "kernel sources to build module - where ??"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by jackowski on 2005-05-05
I'd like to install current running kernel source. It's default kernel from hoary 5.04. I was trying apt-get install kernel-source linux-source but I cant install them. The only kernel source that apt sees is 2.4.27. I need the source to build fglrx module for my radeon mobility 9200. Here is my sources.list:

## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

  #
  # Gnu Gadu 2 Debian's packages
  #
  deb [http://metro.lezajsk.info/gg2/sarge.old](http://metro.lezajsk.info/gg2/sarge.old) ./
  deb-src [http://metro.lezajsk.info/gg2/sarge.old](http://metro.lezajsk.info/gg2/sarge.old) ./

  # KDE-Bluetooth
 deb [http://fred.hexbox.de/debian](http://fred.hexbox.de/debian) ./

  # Backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

 # Debian
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=jackowski]I'd like to install current running kernel source. It's default kernel from hoary 5.04. I was trying apt-get install kernel-source linux-source but I cant install them. The only kernel source that apt sees is 2.4.27. I need the source to build fglrx module for my radeon mobility 9200. Here is my sources.list:

## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

  #
  # Gnu Gadu 2 Debian's packages
  #
  deb [http://metro.lezajsk.info/gg2/sarge.old](http://metro.lezajsk.info/gg2/sarge.old) ./
  deb-src [http://metro.lezajsk.info/gg2/sarge.old](http://metro.lezajsk.info/gg2/sarge.old) ./

  # KDE-Bluetooth
 deb [http://fred.hexbox.de/debian](http://fred.hexbox.de/debian) ./

  # Backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

 # Debian
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main[/QUOTE]
 Look for kernel-headers, not kernel-source.

---

### Post by jackowski on 2005-05-06
[QUOTE=Alexander Kirillov]Look for kernel-headers, not kernel-source.[/QUOTE]

the only kernel headers which apt (exactly synaptic) sees are 2.5.999-test7-bk-17 and this kernel source is not the source of my running kernel  :-?

---

### Post by cutOff on 2005-05-06
[QUOTE=jackowski]the only kernel headers which apt (exactly synaptic) sees are 2.5.999-test7-bk-17 and this kernel source is not the source of my running kernel  :-?[/QUOTE]
```
$ sudo apt-cache search linux-headers
```

---

