---
title: "64-Bit upgrade breezy-&gt;dapper failed"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by pointym5 on 2006-06-03
I'm stuck with upgrade-manager and Synaptic producing a variety of unhelpful errors.  The packages causing problems are:

ia32-libs
openoffice.org-common
openoffice.org-core
language-support-en

They're currently "broken".  When I attempt to let them install, the ia32 package fails (it says) because it can't create /usr/lib32/libGL.so.2.1.  If I try to remove the packages, that fails with all sorts of errors about the fact that they're in a state of incompleteness.  That library file does not exist, and since it's running as root the error is almost certainly bogus. One weirdness is that it prints the pathname in the error with a leading ".", leading me to wonder whether the package is just broken.

Do Ubuntu upgrades **ever** work?  They've never worked for me on the several machines I've got.  **Never.**

---

### Post by pointym5 on 2006-06-03
Using "dpkg -r" to nuke the busted packages allowed me to complete the upgrade. Maybe.

---

### Post by pointym5 on 2006-06-03
Actually no - there seems to be a problem with the "ia32-libs" package for openoffice; it simply will not install.

---

### Post by HellSpawn on 2006-06-03
Hello!!

I just upgraded from Ubuntu 5.10 to 6.06 and encounter some problems too with one package... I cannot get ia32-libs Upgraded, it keeps getting incomplete, not even 'apt-get remove' works... I tryed reinstalling the packege and tried Upgrading and removeing but still gets the same error...

So, right know I'm without OpenOffice wich depends on this packege... I'm stuck, I even tried booting from the Live CD with chroot

```

igor@ubuntu:~$ sudo apt-get install --fix-missing
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ia32-libs
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 169153 files and directories currently installed.)
Removing ia32-libs ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/bin/ldd to /usr/bin/ldd.ia32-libs by ia32-libs'  found `diversion of /usr/bin/ldd to /usr/bin/ldd.amd64 by ia32-libs'
dpkg: error processing ia32-libs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ia32-libs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

igor@ubuntu:~$ sudo apt-get remove ia32-libs
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ia32-libs
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169153 files and directories currently installed.)
Removing ia32-libs ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/bin/ldd to /usr/bin/ldd.ia32-libs by ia32-libs'  found `diversion of /usr/bin/ldd to /usr/bin/ldd.amd64 by ia32-libs'
dpkg: error processing ia32-libs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ia32-libs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any Ideas??:scratch: :confused: 

Thanks for your attention

---

### Post by pointym5 on 2006-06-04
Here's my sources.list, which I believe to be a clean dapper list:```
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted


deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

Here's what happens when I attempt to install "ia32-libs":
```
$ apt-get install ia32-libs                
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/3837kB of archives.
After unpacking 9310kB of additional disk space will be used.
(Reading database ... 91469 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_1.4ubuntu19_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've run that with *strace* but I can't tell what exactly it is that *dpkg* is complaining about.

---

### Post by pointym5 on 2006-06-04
OK, I don't know how or why things got messed up, but the root problem was that something in the ia32-libs installer was trying to create a library in "/usr/lib32/nvidia".  That directory did not exist on my machine. The error message produced was therefore misleading, as the filename it contained was not actually the file causing the problem.

Creating /usr/lib32/nvidia allowed the install of that package to proceed.

---

### Post by HellSpawn on 2006-06-04
I thought we had the same problem... I hope my problem has a solution most like yours... :(

This is my sources.list
```

deb-src http://ve.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://ve.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://ve.archive.ubuntu.com/ubuntu dapper universe

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

## Backports
# deb http://ubuntu-backports.mirrormax.net/ dapper-backports-staging main universe multiverse restricted
# deb http://ubuntu-backports.mirrormax.net/ dapper-extras-staging main universe multiverse restricted

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted


```

---

### Post by HellSpawn on 2006-06-04
Got a solution... :D

I looked into my /var/libs/dpkg/status file and found this:

```

Package: ia32-libs
Status: deinstall ok half-installed
Priority: optional
Section: libs
Installed-Size: 22732
Maintainer: Bdale Garbee <bdale@gag.com>
Architecture: amd64
Version: 1.4ubuntu4
Config-Version: 1.4ubuntu4
Replaces: ia32-libs-openoffice.org
Depends: lsb-release, lib32gcc1, lib32z1
Description: ia32 shared libraries for use on amd64 and ia64 systems
 This package contains runtime libraries for the ia32/i386
 architecture, configured for use on an amd64 or ia64 Debian system running
 a 64-bit kernel.

```

So... I change it to:

```

Package: ia32-libs
Status: purge ok not-installed
Priority: optional
Section: libs
Architecture: amd64

```

And then I was able to install ia32-libs from Ubuntu 6.06 Dapper Drake :D
Then Installed uduntu-desktop, so OpenOffice.org is working again!!

---

