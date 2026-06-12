---
title: "problem with some packages"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by v3rtigo on 2006-03-03
From some reason i have few packages that refuse to install

thats what i get if i try to install

```
E: evolution: subprocess post-installation script returned error exit
status 1
E: evolution-exchange: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gij-4.0: subprocess post-installation script returned error exit
status 127
E: gij: dependency problems - leaving unconfigured
E: java-gcj-compat: dependency problems - leaving unconfigured
E: libservlet2.3-java: dependency problems - leaving unconfigured
E: libhsqldb-java: dependency problems - leaving unconfigured

```

---

### Post by welsh_spud on 2006-03-03
Have you changed your sources.list in /etc/apt/ to connect to any other repositories? ie. for MP3 codecs, Win32 codecs etc

---

### Post by v3rtigo on 2006-03-03
yea

---

### Post by welsh_spud on 2006-03-03
Can you post your sources.list file here so we can see if there is an error with it? Also you may want to try typing:-

sudo apt-get -f install

in a command line

---

### Post by v3rtigo on 2006-03-04
sudo apt-get -f install

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up evolution (2.4.1-0ubuntu7) ...
/usr/share/gconf/schemas/apps_evolution_calendar-2.4.schemas:5198: parser error : expected '>'
        <short>&#1062;&#1074;&#1103;&#1090; &#1085;&#1072; &#1087;&#1088;&#1086;&#1089;&#1088;&#1984;&#1086;&#1086;&#1095;&#1077;&#1085;&#1080;&#1090;&#1077; &#1079;&#1072;&#1076;&#1072;&#1095;&#1080;</sho<lon
                                                                           ^
/usr/share/gconf/schemas/apps_evolution_calendar-2.4.schemas:5198: parser error : Opening and ending tag mismatch: short line 5198 and sho
        <short>&#1062;&#1074;&#1103;&#1090; &#1085;&#1072; &#1087;&#1088;&#1086;&#1089;&#1088;&#1984;&#1086;&#1086;&#1095;&#1077;&#1085;&#1080;&#1090;&#1077; &#1079;&#1072;&#1076;&#1072;&#1095;&#1080;</sho<lon
                                                                           ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.4.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.4.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.4.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gij-4.0 (4.0.1-4ubuntu9) ...
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 670: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
dpkg: error processing gij-4.0 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.0 (>= 4.0.1-2); however:
  Package gij-4.0 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.0; however:
  Package gij-4.0 is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.3-java:
 libservlet2.3-java depends on java-gcj-compat | java1-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
dpkg: error processing libservlet2.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on libservlet2.3-java; however:
  Package libservlet2.3-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evolution
 evolution-exchange
 evolution-plugins
 gij-4.0
 gij
 java-gcj-compat
 libservlet2.3-java
 libhsqldb-java
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


sources.list

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://deb.opera.com/opera/ etch non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://kubuntu.org/packages/kde351 breezy main

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## created by arnieamuleadded

```

---

### Post by v3rtigo on 2006-03-10
bump

---

### Post by Xian on 2006-03-10
What is the output of this command:

$ sudo dpkg --configure -a

---

### Post by v3rtigo on 2006-03-11
```

 sudo dpkg --configure -a
Setting up gij-4.0 (4.0.1-4ubuntu9) ...
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 670: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
dpkg: error processing gij-4.0 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.12-10-386-nvidia-legacy:
 linux-restricted-modules-2.6.12-10-386-nvidia-legacy depends on linux-image-2.6.12-10-386; however:
  Package linux-image-2.6.12-10-386 is not installed.
dpkg: error processing linux-restricted-modules-2.6.12-10-386-nvidia-legacy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.0; however:
  Package gij-4.0 is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.0 (>= 4.0.1-2); however:
  Package gij-4.0 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
Setting up evolution (2.4.1-0ubuntu7) ...
/usr/share/gconf/schemas/apps_evolution_calendar-2.4.schemas:5198: parser error : expected '>'
        <short>&#1062;&#1074;&#1103;&#1090; &#1085;&#1072; &#1087;&#1088;&#1086;&#1089;&#1088;&#1984;&#1086;&#1086;&#1095;&#1077;&#1085;&#1080;&#1090;&#1077; &#1079;&#1072;&#1076;&#1072;&#1095;&#1080;</sho<lon
                                                                           ^
/usr/share/gconf/schemas/apps_evolution_calendar-2.4.schemas:5198: parser error : Opening and ending tag mismatch: short line 5198 and sho
        <short>&#1062;&#1074;&#1103;&#1090; &#1085;&#1072; &#1087;&#1088;&#1086;&#1089;&#1088;&#1984;&#1086;&#1086;&#1095;&#1077;&#1085;&#1080;&#1090;&#1077; &#1079;&#1072;&#1076;&#1072;&#1095;&#1080;</sho<lon
                                                                           ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libservlet2.3-java:
 libservlet2.3-java depends on java-gcj-compat | java1-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
dpkg: error processing libservlet2.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on libservlet2.3-java; however:
  Package libservlet2.3-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.4.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.4.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.4.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.0
 linux-restricted-modules-2.6.12-10-386-nvidia-legacy
 java-gcj-compat
 gij
 evolution
 libservlet2.3-java
 libhsqldb-java
 evolution-exchange
 evolution-plugins


```

---

### Post by v3rtigo on 2006-03-27
up

---

