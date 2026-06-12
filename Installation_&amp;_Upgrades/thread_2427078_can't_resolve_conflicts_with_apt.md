---
title: "can't resolve conflicts with apt"
date: 2019-09-17
forum: Installation &amp; Upgrades
---

### Post by reggler on 2019-09-17
Hi

I have conflicts with apt that I have not been able to resolve: I'm running on 16.04 LTS and wanted to upgrade but got stuck and now I need to install an additional piece of software but of course am getting the same kind of apt troubles from before:
```
$ sudo apt install aftp
[sudo] password for ron:
ron@jpax-build07:~/scripts$ sudo apt install atftp
[sudo] password for ron:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is to be installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not going to be installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is to be installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is to be installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is to be installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is to be installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not going to be installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not installed or
                                virtualbox-5.1 but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


```

I also have an opopen thread on askubuntu.com but didn't get it resolved.... :(
It looks like I'm having two offending packages: python3-xapian1.3 & python3-xapian which I don't think I need anymore anyways but  I'm unclear of how I correctly remove them without screwing my system up further.
Can anyone here provide me some further help? I'll make sure to cross update the two open threads when there's any updates on either side.

Thank you!

---

### Post by SeijiSensei on 2019-09-17
First, did you try running "sudo apt --fix-broken install"?

Also did you run "sudo apt update" before trying to install?

---

### Post by reggler on 2019-09-17
Yes and yes, I pastyed the results of "sudo apt --fix-broken install" above too and here's what i get from update:
```

$ sudo apt update
[sudo] password for ron:
Hit:1 http://ca.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Hit:4 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:5 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [111 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main Sources [154 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [739 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [591 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [289 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [76.1 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [76.1 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [76.1 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [76.1 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [79.7 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [124 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [194 kB]
Fetched 583 kB in 6s (89.8 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
39 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

---

### Post by mc4man on 2019-09-17
How did you try to upgrade 16.04?
It appears you added some disco packages somehow,  probably a very poor idea...

---

### Post by reggler on 2019-09-18
> **mc4man said:**
> How did you try to upgrade 16.04?
It appears you added some disco packages somehow,  probably a very poor idea...

I first tried to **dist-upgrade** and when that failed, I tried **sudo apt update** then **sudo apt full-upgrade** but that kept failing too. I don't know if that first dist-upgrade I ran messed up everything...?

---

### Post by mc4man on 2019-09-18
For info sake post
```
apt-cache policy cmake-data libglib2.0-bin libglib2.0-0 python3-minimal python3-apt python3
```

---

### Post by reggler on 2019-09-18
```

s$ apt-cache policy cmake-data libglib2.0-bin libglib2.0-0 python3-minimal python3-apt python3
cmake-data:
  Installed: 3.13.4-1
  Candidate: 3.13.4-1
  Version table:
 *** 3.13.4-1 100
        100 /var/lib/dpkg/status
     3.5.1-1ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
     3.5.1-1ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main i386 Packages
libglib2.0-bin:
  Installed: 2.60.0-1
  Candidate: 2.60.0-1
  Version table:
 *** 2.60.0-1 100
        100 /var/lib/dpkg/status
     2.48.2-0ubuntu4.4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     2.48.0-1ubuntu4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libglib2.0-0:
  Installed: 2.48.2-0ubuntu4.4
  Candidate: 2.48.2-0ubuntu4.4
  Version table:
 *** 2.48.2-0ubuntu4.4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.48.0-1ubuntu4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python3-minimal:
  Installed: 3.7.3-1
  Candidate: 3.7.3-1
  Version table:
 *** 3.7.3-1 100
        100 /var/lib/dpkg/status
     3.5.1-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python3-apt:
  Installed: 1.8.4
  Candidate: 1.8.4
  Version table:
 *** 1.8.4 100
        100 /var/lib/dpkg/status
     1.1.0~beta1ubuntu0.16.04.5 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1.1.0~beta1build1 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python3:
  Installed: 3.5.1-3
  Candidate: 3.5.1-3
  Version table:
 *** 3.5.1-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status


```

What does the "priority" number mean?

---

### Post by mc4man on 2019-09-18
You've installed a number of packages that didn't come from xenial repos. They didn't install themselves so what did you do?

The cmake-data is no big deal, it could just be removed..
However the glib and python3 packages that are wrong versions would be much trickier, one method would be to identify **all **of the wrong version package and acquire the proper xenial ones. It then might be possible to install them as a group.
If you handle the replacement wrong you'll probably not be able to reboot and log in..

A bit of a chore and mess you've created.
Atm cmake-data, libglib2.0-bin, python3-apt & python3-minimal are wrong versions, likely some other python3 wrong packages, maybe another glib package or 2..

---

### Post by rsteinmetz70112 on 2019-09-18
It appears you are still running 16.04 packages. I think you will need to configure the packages that are already downloaded to get the system working

Try ```
sudo dpkg --configure -a
```

Post the output, that may configure some of the packages and you will probably still have some broken packages. 
Then run:

```
apt install -f
```
The above command is the same as ```
apt --fix-broken install
```

That might fix some more.

You may have to update the libraries again and continue to chip away at the errors.

The basic problem seems to be a bunch of python stuff is not configured and a bunch of stuff depends on python.
What most likely happened was that after downloading the packages do-release-upgrade failed leaving a bunch of unmet dependencies.

You most likely can get it to work if you keep at it. I've been able to work through similar problems.

---

### Post by mc4man on 2019-09-19
Please post,
```
apt-cache show libglib2.0-bin python3-minimal
```

---

### Post by reggler on 2019-09-19
> **mc4man said:**
> You've installed a number of packages that didn't come from xenial repos. They didn't install themselves so what did you do?
Hm, I wish I knew to be honest. This machine has been working for me for at least 5 years, I have messed around somewhat but am unable to exactly tell you what I did... :(

> **mc4man said:**
> The cmake-data is no big deal, it could just be removed..
However the glib and python3 packages that are wrong versions would be much trickier, one method would be to identify **all **of the wrong version package and acquire the proper xenial ones. It then might be possible to install them as a group.
If you handle the replacement wrong you'll probably not be able to reboot and log in..

Well, I really hope I won't get there, that would be bad... as this is my primary work machine. It's a virtual machine though and before I started with the upgrade, I asked IT to take a snapshot - for - "just in case..."
> **mc4man said:**
> 
A bit of a chore and mess you've created.
Atm cmake-data, libglib2.0-bin, python3-apt & python3-minimal are wrong versions, likely some other python3 wrong packages, maybe another glib package or 2..
I see... I hope I can get help here to get myself out of this mess! :(

---

### Post by reggler on 2019-09-19
> **rsteinmetz70112 said:**
> It appears you are still running 16.04 packages. I think you will need to configure the packages that are already downloaded to get the system working

Try ```
sudo dpkg --configure -a
```

Post the output, that may configure some of the packages and you will probably still have some broken packages. 
Okay, let's see:
```

dpkg: dependency problems prevent configuration of python3-pil:amd64:
 python3-pil:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-pil:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lxml:amd64:
 python3-lxml:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-lxml:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-brlapi:amd64:
 python3-brlapi:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-brlapi:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-libapparmor:
 python3-libapparmor depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-libapparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python3-xapian (>= 1.4.3-1); however:
  Package python3-xapian is not installed.
  Version of python3-xapian on system, provided by python3-xapian1.3:amd64, is <none>.
 apt-xapian-index depends on python3-apt (>= 0.7.93.2); however:
  Package python3-apt is not configured yet.

dpkg: error processing package apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dev:
 python3-dev depends on python3 (= 3.7.3-1); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lib2to3:
 python3-lib2to3 depends on python3 (>= 3.7.1-1~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-lib2to3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.60.0-1); however:
  Version of libglib2.0-0:amd64 on system is 2.48.2-0ubuntu4.4.

dpkg: error processing package libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distutils:
 python3-distutils depends on python3 (>= 3.7.1-1~); however:
  Version of python3 on system is 3.5.1-3.
 python3-distutils depends on python3-lib2to3 (>= 3.6.4); however:
  Package python3-lib2to3 is not configured yet.

dpkg: error processing package python3-distutils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-pil:amd64
 python3-apt
 python3-lxml:amd64
 python3-brlapi:amd64
 python3-libapparmor
 apt-xapian-index
 python3-dev
 python3-lib2to3
 libglib2.0-bin
 python3-distutils
                     

```
> **rsteinmetz70112 said:**
> 
Then run:

```
apt install -f
```
The above command is the same as ```
apt --fix-broken install
``````

$ sudo apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not installed or
                                virtualbox-5.1 but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

That might fix some more.

You may have to update the libraries again and continue to chip away at the errors.[/QUOTE]
I'll chip away at it at the errors until I get this going again, there really is no alternative at this point...! :(

> **rsteinmetz70112 said:**
> The basic problem seems to be a bunch of python stuff is not configured and a bunch of stuff depends on python.
What most likely happened was that after downloading the packages do-release-upgrade failed leaving a bunch of unmet dependencies.

You most likely can get it to work if you keep at it. I've been able to work through similar problems.
I only need Python for **Xpra** ah now! I've installed **XPRA** from a third party repo and it is running on Python. Might that be the issue?

---

### Post by reggler on 2019-09-20
> **mc4man said:**
> Please post,
```
apt-cache show libglib2.0-bin python3-minimal
```
```

Package: libglib2.0-bin
Status: install ok unpacked
Priority: optional
Section: misc
Installed-Size: 314
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: glib2.0
Version: 2.60.0-1
Config-Version: 2.48.2-0ubuntu4.4
Depends: libglib2.0-0 (= 2.60.0-1), libglib2.0-data, libc6 (>= 2.4), libelf1 (>= 0.142)
Description-en: Programs for the GLib library
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the program files which is used for the libraries
 and others.
Description-md5: b999624c61f8058d0201077f097c87ed
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Homepage: http://www.gtk.org/

Package: libglib2.0-bin
Architecture: amd64
Multi-Arch: foreign
Source: glib2.0
Version: 2.60.0-1
Config-Version: 2.48.2-0ubuntu4.4
Depends: libglib2.0-0 (= 2.60.0-1), libglib2.0-data, libc6 (>= 2.4), libelf1 (>= 0.142)
Description-en: Programs for the GLib library
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the program files which is used for the libraries
 and others.
Description-md5: b999624c61f8058d0201077f097c87ed
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Homepage: http://www.gtk.org/

Package: libglib2.0-bin
Architecture: amd64
Version: 2.48.2-0ubuntu4.4
Multi-Arch: foreign
Priority: optional
Section: misc
Source: glib2.0
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 305
Depends: libc6 (>= 2.4), libelf1 (>= 0.142), libglib2.0-0 (= 2.48.2-0ubuntu4.4), libglib2.0-data
Filename: pool/main/g/glib2.0/libglib2.0-bin_2.48.2-0ubuntu4.4_amd64.deb
Size: 39510
MD5sum: 3d33086d0b376f6b0db3e2af78ac2a87
SHA1: bc3fccf0712b198bcea7287da2375609efcdb5b2
SHA256: de92080d22cd4fc2591a886c3914acac26bd8a008a6813753b6c23f87c0684ed
Homepage: http://www.gtk.org/
Description-en: Programs for the GLib library
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the program files which is used for the libraries
 and others.
Description-md5: b999624c61f8058d0201077f097c87ed
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, xubuntu-core, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntu-gnome-desktop,
 ubuntu-touch-core, ubuntu-touch, ubuntu-touch, ubuntu-sdk, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-mate-cloudtop
Supported: 5y

Package: libglib2.0-bin
Priority: optional
Section: misc
Installed-Size: 1681
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: glib2.0
Version: 2.48.0-1ubuntu4
Replaces: libglib2.0-0 (<< 2.25.11-2), libglib2.0-dev (<< 2.25.11-2)
Depends: libc6 (>= 2.4), libelf1 (>= 0.142), libglib2.0-0 (= 2.48.0-1ubuntu4), libglib2.0-data
Conflicts: libglib2.0-0 (<< 2.25.11-2)
Filename: pool/main/g/glib2.0/libglib2.0-bin_2.48.0-1ubuntu4_amd64.deb
Size: 39404
MD5sum: da0cbb24ac7580202ddeea406b133aba
SHA1: 56fd8779be7236d861c7fb32f1c0282eb01d3013
SHA256: 1e35574846cc62c8f4ca2d4ffd25133269a4bda51fa8346b7c2bd08b4e4937bc
Description-en: Programs for the GLib library
GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the program files which is used for the libraries
 and others.
Description-md5: b999624c61f8058d0201077f097c87ed
Multi-Arch: foreign
Homepage: http://www.gtk.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, xubuntu-core, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntu-gnome-desktop, ubuntu-touch-core, ubuntu-touch, ubuntu-touch, ubuntu-sdk, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-mate-cloudtop

Package: python3-minimal
Status: install ok installed
Priority: important
Section: python
Installed-Size: 121
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: allowed
Source: python3-defaults
Version: 3.7.3-1
Depends: dpkg (>= 1.13.20)
Pre-Depends: python3.7-minimal (>= 3.7.3-1~)
Description: minimal subset of the Python language (default python3 version)
 This package contains the interpreter and some essential modules.  It's used
 in the boot process for some basic tasks.
 See /usr/share/doc/python3.7-minimal/README.Debian for a list of the modules
 contained in this package.
Description-md5: 5b7364c4bab10b1e826d322aee88ed9c
Original-Maintainer: Matthias Klose <doko@debian.org>
Homepage: https://www.python.org/

Package: python3-minimal
Priority: important
Section: python
Installed-Size: 120
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Source: python3-defaults
Version: 3.5.1-3
Replaces: python3 (<< 3.3.2-13~), python3.1 (<< 3.1-2)
Depends: python3.5-minimal (>= 3.5.1-2~), dpkg (>= 1.13.20)
Breaks: idle3 (<< 3.1), python3 (<< 3.3.2-13~), python3-all (<< 3.1), python3-all-dbg (<< 3.1), python3-all-dev (<< 3.1), python3-dbg (<< 3.1), python3-dev (<< 3.1), python3-examples (<< 3.1)
Filename: pool/main/p/python3-defaults/python3-minimal_3.5.1-3_amd64.deb
Size: 23300
MD5sum: fd2ecfa165ce0251acfb4f9c69e5235a
SHA1: bd4bf8e8495a1d876b068096e2e952a96d1a8d8a
SHA256: a6f0eef651128fa2ef12266c2a3b665a770f742aad8f3ac49ebd2ab45d260a55
Description-en_CA: minimal subset of the Python language (default python3 version)
 This package contains the interpreter and some essential modules.  It's
 used in the boot process for some basic tasks. See
 /usr/share/doc/python3.5-minimal/README.Debian for a list of the modules
 contained in this package.
Description-md5: f17f06e9e02ce802bf363248805d544c
Multi-Arch: allowed
Homepage: http://www.python.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal, ubuntu-core, ubuntu-core, ubuntu-sdk-libs-tools, ubuntu-sdk

```

---

### Post by mc4man on 2019-09-20
You started this thread with "I'm running on 16.04 LTS and wanted to upgrade..." but when asked in post 4 you stated "dist-upgrade and when that failed, I tried sudo apt update then sudo apt full-upgrade .." 
Those commands have nothing to with a Release-upgrade..,

So - where you always just trying to upgrade 16.04 itself or you trying to upgrade 16.04 to a new Release? ( like 18.04 or 19.04 or 19.10
If the later, then again, how did you attempt this.

.(- side note, what is aftp , there is no such package in Ubuntu

---

### Post by rsteinmetz70112 on 2019-09-20
The python3 version for 16.04 is 3.5.1-3 where did python 3.7 come from?
Was it part of the failed  software install? or did you install it from a PPA? 
That seems to be the root of your problems. The default version for 18.04 is 3.6.5-3

---

### Post by reggler on 2019-09-20
> **rsteinmetz70112 said:**
> The python3 version for 16.04 is 3.5.1-3 where did python 3.7 come from?
I believe it came in with **XPRA** with repositories I got from [https://xpra.org/trac/wiki/Download#Linux](https://xpra.org/trac/wiki/Download#Linux)
I just killed all my xpra sessions and tried to remove it - but that of course isn't working now either:
```

$ xpra list
Found the following xpra sessions:
        UNKNOWN session at :200
        UNKNOWN session at :9999
Re-probing unknown sessions: :200, :9999
xpra stop :     UNKNOWN session at :200 (cleaned up)
        UNKNOWN session at :9999 (cleaned up)
ron@jpax-build07:~/scripts$ xpra stop :200
xpra initialization error: connection failed: [Errno 2] No such file or directory
ron@jpax-build07:~/scripts$ xpra stop :999
xpra initialization error: connection failed: [Errno 2] No such file or directory
ron@jpax-build07:~/scripts$ xpra stop :9999
xpra initialization error: connection failed: [Errno 2] No such file or directory
ron@jpax-build07:~/scripts$ xpra list
xpra initialization error: No xpra sessions found
ron@jpax-build07:~/scripts$ sudo apt remove xpra
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is to be installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not going to be installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is to be installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is to be installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is to be installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is to be installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not going to be installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```
> **rsteinmetz70112 said:**
> Was it part of the failed  software install? or did you install it from a PPA? 
That seems to be the root of your problems. The default version for 18.04 is 3.6.5-3
Okay, how do I best get rid of it then?

---

### Post by reggler on 2019-09-20
> **mc4man said:**
> You started this thread with "I'm running on 16.04 LTS and wanted to upgrade..." but when asked in post 4 you stated "dist-upgrade and when that failed, I tried sudo apt update then sudo apt full-upgrade .." 
Those commands have nothing to with a Release-upgrade..,

So - where you always just trying to upgrade 16.04 itself or you trying to upgrade 16.04 to a new Release? ( like 18.04 or 19.04 or 19.10
If the later, then again, how did you attempt this.

.(- side note, what is aftp , there is no such package in Ubuntu
I would like to do a full release-upgrade and tried it with **sudo do-release-upgrade**. I just tried this now again to see what I get but now:
```

$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.
$ lsb-release -a
Traceback (most recent call last):
  File "/usr/lib/python3.7/dbm/gnu.py", line 4, in <module>
    from _gdbm import *
ModuleNotFoundError: No module named '_gdbm'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 7, in <module>
    import dbm.gnu as gdbm
  File "/usr/lib/python3.7/dbm/gnu.py", line 6, in <module>
    raise ImportError(str(msg) + ', please install the python3-gdbm package')
ImportError: No module named '_gdbm', please install the python3-gdbm package

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 27, in <module>
    from CommandNotFound.util import crash_guard
  File "/usr/lib/python3/dist-packages/CommandNotFound/__init__.py", line 3, in <module>
    from CommandNotFound.CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 9, in <module>
    import gdbm
ModuleNotFoundError: No module named 'gdbm'


```
but I haven't really updated anything yet....

---

### Post by rsteinmetz70112 on 2019-09-20
Is apt working? One of the packages I see that is not configuring is apt-python3.7

You could try this.

Remove any non ubuntu repositories and PPAs from your sources. 

Then remove any uninstalled or partially installed packages with :
```
sudo apt update
sudo apt clean
sudo apt autoremove
sudo apt install -f
sudo dpkg --configure -a 
```

If get you a working  python 3.5.1 You can then work through any remaining broken python packages to get them to work or purge them.


I think if you want to **"do-release-upgrade"** it will be necessary to get rid ofthe  Python 3.7 packages and go back to 3.5.1-3. 
```
sudo dpkg --list |grep python3.7
```
Before you **"do-release-upgrade"** make sure you clear any problems and that:
```
sudo dpkg --configure
sudo apt install -f 
```
run cleanly with no errors. Do not go further until they do.

Once you have a fully updated clean system you can:
```
sudo apt upgrade
sudo full-upgrade
do-release-upgrade
```
When you get to 18/04 you can probably install what you want.

---

### Post by mc4man on 2019-09-20
Your best bet is to acquire ALL of the  Disco era (19.04/19.10) packages you've either installed or were attempted to install  but were not configured, for example with glib  you need 
 libglib2.0-bin  2.48.2-0ubuntu4.4
for python3-minimal,
 python3-minimal   3.5.1-3 
ect.,  ect.
Still don't think you're telling all, those disco era (19.04/19.10) packages didn't show up thru any upgrade command, you either downloaded them or more likely edited your sources in an initial attempt to Upgrade 16.04 to ....?

---

### Post by reggler on 2019-09-20
> **rsteinmetz70112 said:**
> Is apt working? One of the packages I see that is not configuring is apt-python3.7

You could try this.

Remove any non ubuntu repositories and PPAs from your sources. 

Then remove any uninstalled or partially installed packages with :
```

$ sudo apt update
[sudo] password for ron:
Hit:1 http://ca.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [111 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main Sources [154 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main Sources [339 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [595 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [260 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [748 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [291 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [860 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [76.2 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [84.0 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [396 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [1,033 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [458 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [402 kB]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [187 kB]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [124 kB]
Get:21 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [324 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [194 kB]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:24 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [238 kB]
Get:25 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [764 kB]
Get:26 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [695 kB]
Get:27 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [320 kB]
Get:28 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [274 kB]
Get:29 http://ca.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [413 kB]
Get:30 http://ca.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Get:31 http://ca.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]
Get:32 http://ca.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:33 http://ca.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,328 B]
Fetched 9,696 kB in 27s (357 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
45 packages can be upgraded. Run 'apt list --upgradable' to see them.
ron@jpax-build07:~/scripts$ 
sudo apt clean
sudo apt autoremove
sudo apt install -f
sudo dpkg --configure -a 
```
```

ron@jpax-build07:~/scripts$ sudo apt update
[sudo] password for ron:

ron@jpax-build07:~/scripts$ sudo apt clean
[sudo] password for ron:
ron@jpax-build07:~/scripts$ sudo apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not installed or
                                virtualbox-5.1 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
ron@jpax-build07:~/scripts$ sudo apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.5.1-3 is installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is installed
               Recommends: python3-olefile but it is not installable
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not installed or
                                virtualbox-5.1 but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
ron@jpax-build07:~/scripts$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of python3-pil:amd64:
 python3-pil:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-pil:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lxml:amd64:
 python3-lxml:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-lxml:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-brlapi:amd64:
 python3-brlapi:amd64 depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-brlapi:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-libapparmor:
 python3-libapparmor depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-libapparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python3-xapian (>= 1.4.3-1); however:
  Package python3-xapian is not installed.
  Version of python3-xapian on system, provided by python3-xapian1.3:amd64, is <none>.
 apt-xapian-index depends on python3-apt (>= 0.7.93.2); however:
  Package python3-apt is not configured yet.

dpkg: error processing package apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dev:
 python3-dev depends on python3 (= 3.7.3-1); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lib2to3:
 python3-lib2to3 depends on python3 (>= 3.7.1-1~); however:
  Version of python3 on system is 3.5.1-3.

dpkg: error processing package python3-lib2to3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.60.0-1); however:
  Version of libglib2.0-0:amd64 on system is 2.48.2-0ubuntu4.4.

dpkg: error processing package libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distutils:
 python3-distutils depends on python3 (>= 3.7.1-1~); however:
  Version of python3 on system is 3.5.1-3.
 python3-distutils depends on python3-lib2to3 (>= 3.6.4); however:
  Package python3-lib2to3 is not configured yet.

dpkg: error processing package python3-distutils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-pil:amd64
 python3-apt
 python3-lxml:amd64
 python3-brlapi:amd64
 python3-libapparmor
 apt-xapian-index
 python3-dev
 python3-lib2to3
 libglib2.0-bin
 python3-distutils
ron@jpax-build07:~/scripts$

```

> **rsteinmetz70112 said:**
> If get you a working  python 3.5.1 You can then work through any remaining broken python packages to get them to work or purge them.

An attempt to purge the python3-dev package looks like:
```

$ sudo apt purge python3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 apt-xapian-index : Depends: python3-xapian (>= 1.4.3-1)
 cmake : Depends: cmake-data (= 3.5.1-1ubuntu3) but 3.13.4-1 is to be installed
 libcairo2-dev:i386 : Depends: libfontconfig1-dev:i386 (>= 2.2.95) but it is not going to be installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.60.0-1) but 2.48.2-0ubuntu4.4 is to be installed
 libglib2.0-dev:i386 : Depends: libglib2.0-bin:i386 (= 2.48.2-0ubuntu4.4)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is to be installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is to be installed
 python3-apt : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-brlapi : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-distutils : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-lib2to3 : Depends: python3 (>= 3.7.1-1~) but 3.5.1-3 is to be installed
 python3-libapparmor : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-lxml : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
 python3-pil : Depends: python3 (>= 3.7~) but 3.5.1-3 is to be installed
               Recommends: python3-olefile but it is not installable
 python3-sip-dev : Depends: python3-dev but it is not going to be installed
 testdrive-common : Depends: qemu-kvm or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox (>= 4.0) but it is not going to be installed
                    Recommends: kvm-pxe but it is not installable
 virtualbox-ext-pack : Depends: virtualbox (< 5.1.38-dfsg-z) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
                       Depends: virtualbox (>= 5.1.38-dfsg-0~) but it is not going to be installed or
                                virtualbox-5.1 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```
How am I supposedto "get them to work or purge them"?
> **rsteinmetz70112 said:**
> 
I think if you want to **"do-release-upgrade"** it will be necessary to get rid ofthe  Python 3.7 packages and go back to 3.5.1-3. 
```
sudo dpkg --list |grep python3.7
```
Before you **"do-release-upgrade"** make sure you clear any problems and that:
```
sudo dpkg --configure
sudo apt install -f 
```
run cleanly with no errors. Do not go further until they do.

Once you have a fully updated clean system you can:
```
sudo apt upgrade
sudo full-upgrade
do-release-upgrade
```
When you get to 18/04 you can probably install what you want.

---

### Post by reggler on 2019-09-20
> **mc4man said:**
> Your best bet is to acquire ALL of the  Disco era (19.04/19.10) packages you've either installed or were attempted to install  but were not configured, for example with glib  you need 
 libglib2.0-bin  2.48.2-0ubuntu4.4
for python3-minimal,
 python3-minimal   3.5.1-3 
ect.,  ect.
Still don't think you're telling all, those disco era (19.04/19.10) packages didn't show up thru any upgrade command, you either downloaded them or more likely edited your sources in an initial attempt to Upgrade 16.04 to ....?

So if I understand right, you suggest to manually download & upgrade all the files where @rsteinmetz70112 suggests to backup to the starting point and upgrade from there, what's the best thing to proceed? 
If I chose the method suggested in this post, would I go to [https://packages.ubuntu.com/](https://packages.ubuntu.com/), search the package (libglib2) and download the am64 version of the deb package, e.g. [http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.60.0-1ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.60.0-1ubuntu0.1_amd64.deb) only the version doesn't seem to align with what you entered above... and then install the packages using **sudo dpkg -i file.deb**?

---

### Post by rsteinmetz70112 on 2019-09-23
Before we do anything dangerour lets find out a little more about the state of your system. Run the following commands and post the results.
```
$ ls /usr/lib | grep python
$ ls -ld /usr/bin/python
$ ls -ld /usr/bin/python3
$ which python
$ python --version
```

To remove a  package:
```
sudo apt remove <package name>
```
I'm not sure if that will work on partially installed packages if not try.
```
sudo apt purge <package name>
```
or combine the two 
```
sudo apt remove --purge <package name>
```
I'd be careful and remove them one at a time. 
The command should include the version number the standard Ubuntu would be something like apt-python3.7

Python-minimal is a pretty important package breaking it could break all sorts of stuff. 

This seems to me likely to be the most critical package holding up the works since the 3.7 version is already installed.

>  python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.7.3-1 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.7.3-1 is installed

Before doing anything irreversible you might want to try:
```
sudo apt install python3-minimal libpython3-stdlib --reinstall --simulate
```
This should run the command without actually doing anything but should also show you what the command would do without the --simulate
to make sure it will try to download and install 3.5.1-3 over the existing 3.7 packages.

In fact you might want to download the debs for python3-minimal  or get a Ubuntu 16.04 iso and add it to your sources before you attempt to remove anything so if apt breaks you will still have them available

---

### Post by reggler on 2019-09-24
> **rsteinmetz70112 said:**
> Before we do anything dangerour lets find out a little more about the state of your system. Run the following commands and post the results.
```
$ ls /usr/lib | grep python
$ ls -ld /usr/bin/python
$ ls -ld /usr/bin/python3
$ which python
$ python --version
```

To remove a  package:
```
sudo apt remove <package name>
```
I'm not sure if that will work on partially installed packages if not try.
```
sudo apt purge <package name>
```
or combine the two 
```
sudo apt remove --purge <package name>
```
I'd be careful and remove them one at a time. 
The command should include the version number the standard Ubuntu would be something like apt-python3.7

Python-minimal is a pretty important package breaking it could break all sorts of stuff. 

This seems to me likely to be the most critical package holding up the works since the 3.7 version is already installed.
[/QOTE]
```

$ ls /usr/lib |grep python
python2.7
python3
python3.5
python3.7
python3.8
$ ls -ld /usr/bin/python
lrwxrwxrwx 1 root root 9 Nov 23  2017 /usr/bin/python -> python2.7
$ ls -ld /usr/bin/python3
lrwxrwxrwx 1 root root 9 Mar 26 03:25 /usr/bin/python3 -> python3.7
$ which python
/usr/bin/python
$ python --version
Python 2.7.12

```
Let's see, just making sure that I understand. the Python3.8 library seems to be a bit out of place, why does Python3 not link to the 3.8, should it? 

Now, I have not gone ahead and removed or purged anything else yet. I've also got the following:
```

$ ls -l /usr/bin/python*
lrwxrwxrwx 1 root root       9 Nov 23  2017 /usr/bin/python -> python2.7
lrwxrwxrwx 1 root root       9 Nov 23  2017 /usr/bin/python2 -> python2.7
lrwxrwxrwx 1 root root      15 Jul 25 09:29 /usr/bin/python2.5 -> /usr/bin/python
-rwxr-xr-x 1 root root 3492656 Aug 22 12:43 /usr/bin/python2.7
lrwxrwxrwx 1 root root      33 Aug 22 12:43 /usr/bin/python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root      16 Nov 23  2017 /usr/bin/python2-config -> python2.7-config
lrwxrwxrwx 1 root root       9 Mar 26 03:25 /usr/bin/python3 -> python3.7
-rwxr-xr-x 2 root root 4460272 Aug 20 13:08 /usr/bin/python3.5
lrwxrwxrwx 1 root root      33 Aug 20 13:08 /usr/bin/python3.5-config -> x86_64-linux-gnu-python3.5-config
-rwxr-xr-x 2 root root 4460272 Aug 20 13:08 /usr/bin/python3.5m
lrwxrwxrwx 1 root root      34 Aug 20 13:08 /usr/bin/python3.5m-config -> x86_64-linux-gnu-python3.5m-config
-rwxr-xr-x 2 root root 4877888 Apr  2 22:39 /usr/bin/python3.7
lrwxrwxrwx 1 root root      33 Apr  2 22:39 /usr/bin/python3.7-config -> x86_64-linux-gnu-python3.7-config
-rwxr-xr-x 2 root root 4877888 Apr  2 22:39 /usr/bin/python3.7m
lrwxrwxrwx 1 root root      34 Apr  2 22:39 /usr/bin/python3.7m-config -> x86_64-linux-gnu-python3.7m-config
lrwxrwxrwx 1 root root      16 Mar 26 03:25 /usr/bin/python3-config -> python3.7-config
lrwxrwxrwx 1 root root      10 Mar 26 03:25 /usr/bin/python3m -> python3.7m
lrwxrwxrwx 1 root root      17 Mar 26 03:25 /usr/bin/python3m-config -> python3.7m-config
lrwxrwxrwx 1 root root      16 Nov 23  2017 /usr/bin/python-config -> python2.7-config

```


[QUOTE=rsteinmetz70112;13891049]
Before doing anything irreversible you might want to try:
```
sudo apt install python3-minimal libpython3-stdlib --reinstall --simulate
```
This should run the command without actually doing anything but should also show you what the command would do without the --simulate
to make sure it will try to download and install 3.5.1-3 over the existing 3.7 packages. Cool, I didn't even know about the **--simulate** option. Great, Thanks!
> **rsteinmetz70112 said:**
> 
In fact you might want to download the debs for python3-minimal  or get a Ubuntu 16.04 iso and add it to your sources before you attempt to remove anything so if apt breaks you will still have them available

Yes, I will download a 16.04 iso and mount it!

Thanks!

---

### Post by rsteinmetz70112 on 2019-09-25
This is getting tricky and you could do real damage to your system if it doesn't work.  We're getting into an area I'm not too familiar with. You might want to consider posting a question to launchpad, the people over there seem have more in depth knowledge.

At least part of the problem is that python3 is linked to python3.7.
```
lrwxrwxrwx 1 root root 9 Mar 26 03:25 /usr/bin/python3 -> python3.7
```
In 16.04 the default is to link to python3.5. Simply changing that link may fix it. Since Python is so important for many things you need to be sure before you do anything or at least be prepared for the concequences. You can really mess up your system.

If a reinstall of python3-minimal from the Ubuntu repositories fixes the python3 link you will probably be fine.

You could try renaming the python3 link (python3.7?) and create a new link python3 to python 3.5 and reboot.
If that doesn't work you could boot into a recovery shell or an iso and fix it.  This option offers the possibility of returning the system to its current state.

You could also try removing python3.7

The real question is are you feeling lucky?

I also think you also want to basically remove all of this:
> -rwxr-xr-x 2 root root 4877888 Apr  2 22:39 /usr/bin/python3.7
lrwxrwxrwx 1 root root      33 Apr  2 22:39 /usr/bin/python3.7-config -> x86_64-linux-gnu-python3.7-config
-rwxr-xr-x 2 root root 4877888 Apr  2 22:39 /usr/bin/python3.7m
lrwxrwxrwx 1 root root      34 Apr  2 22:39 /usr/bin/python3.7m-config -> x86_64-linux-gnu-python3.7m-config
lrwxrwxrwx 1 root root      16 Mar 26 03:25 /usr/bin/python3-config -> python3.7-config
lrwxrwxrwx 1 root root      10 Mar 26 03:25 /usr/bin/python3m -> python3.7m
lrwxrwxrwx 1 root root      17 Mar 26 03:25 /usr/bin/python3m-config -> python3.7m-config
lrwxrwxrwx 1 root root      16 Nov 23  2017 /usr/bin/python-config -> python2.7-config

In any event good luck.

---

### Post by reggler on 2019-09-26
Okay,

I've openbed a thread on launchpad  using the same title at [https://answers.launchpad.net/ubuntu/+question/684315](https://answers.launchpad.net/ubuntu/+question/684315) . 
The firs request was:
> For diagnostic purposes please provide the output of the following commands (even if that information partly is already available on ubuntuforums):

uname -a
lsb_release -crid
grep '^deb ' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
sudo dpkg --audit
apt-cache policy python3 python3-minimal libglib2.0-bin libglib2.0-0

My first conclusion: There are packages from other sources or for higher releases on your system.
Upon which I responded with the following:
> okay,
Here's the requested data:
```

ron@jpax-build07:~/Downloads$ uname -a
Linux jpax-build07 4.15.0-54-generic #58~16.04.1-Ubuntu SMP Mon Jun 24 13:21:41 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
ron@jpax-build07:~/Downloads$ lsb_release -crid
Distributor ID: Ubuntu
Description: Ubuntu 19.04
Release: 19.04
Codename: disco
ron@jpax-build07:~/Downloads$ grep '^deb ' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
grep: /etc/apt/sources.list.d/*.list: No such file or directory
ron@jpax-build07:~/Downloads$ sudo dpkg --audit
[sudo] password for ron:
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 apt-xapian-index maintenance and search tools for a Xapian index of Debian
 cmake-data CMake data files (modules, templates and documentation)
 dwz DWARF compression tool
 libcomerr2:i386 transitional package
 libffi-dev:i386 Foreign Function Interface library (development files)
 libglib2.0-bin Programs for the GLib library
 libpsl5:amd64 Library for Public Suffix List (shared libraries)
 python3-apt Python 3 interface to libapt-pkg
 python3-brlapi:amd64 Braille display access via BRLTTY - Python3 bindings
 python3-dev header files and a static library for Python (default)
 python3-distutils distutils package for Python 3.x
 python3-lib2to3 Interactive high-level object-oriented language (2to3, ve
 python3-libapparmor AppArmor library Python3 bindings
 python3-lxml:amd64 pythonic binding for the libxml2 and libxslt libraries
 python3-pil:amd64 Python Imaging Library (Python3)
 uuid-dev:i386 Universally Unique ID library - headers and static librar

ron@jpax-build07:~/Downloads$ apt-cache policy python3 python3-minimal libglib2.0-bin libglib2.0-0
python3:
  Installed: 3.5.1-3
  Candidate: 3.5.1-3
  Version table:
 *** 3.5.1-3 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
python3-minimal:
  Installed: 3.7.3-1
  Candidate: 3.7.3-1
  Version table:
 *** 3.7.3-1 100
        100 /var/lib/dpkg/status
     3.5.1-3 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
libglib2.0-bin:
  Installed: 2.60.0-1
  Candidate: 2.60.0-1
  Version table:
 *** 2.60.0-1 100
        100 /var/lib/dpkg/status
     2.48.2-0ubuntu4.4 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
  500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
     2.48.0-1ubuntu4 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
libglib2.0-0:
  Installed: 2.48.2-0ubuntu4.4
  Candidate: 2.48.2-0ubuntu4.4
  Version table:
 *** 2.48.2-0ubuntu4.4 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.48.0-1ubuntu4 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
```
Yes, I realize that I somehow got other packages onto my system butI'm not sure how to resolve this mess. 
Hence I appreciate any help I might receive in these regards!


---

### Post by mc4man on 2019-09-27
Well most likely you, in some apparently unknown  manner, tried to release upgrade from 16.04 to 19.04,.
Obviously not going to work out well.

I'd think you could, in some manner, identify all disco packages and downgrade them to 16.04 packages. Maybe aptitude would be useful (assuming you can install it..) or you could  just do manually. 
As long as you have internet and don't break apt/dpkg you can afford to break some packages along the way.
Just don't log out or restart till it's completely fixed. 

Or take about 30 min., some backup media like a flash drive & copy out file/folders of interest & do a fresh install of 18.04
If so and needing to preserve permissions on any files/folders, then compress them before copying, extract after placing in desired location on new install

---

### Post by rsteinmetz70112 on 2019-09-27
Can you reboot successfully? If you don't know don't try.

Do you have a 16.04 kernel on your machine you could boot into?

---

