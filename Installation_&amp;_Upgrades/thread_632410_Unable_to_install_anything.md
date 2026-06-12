---
title: "Unable to install anything"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by itsmepiyush on 2007-12-05
I am not able to install anything in my system(Ubuntu 6.06) after i got an error while installing a software.

When i try to install anything i get the following error.....

specialist@specialist-laptop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20.5) but 2.3.6.ds1-13 is to be installed
  vlc: Depends: liba52-0.7.4 but it is not going to be installed
       Depends: libdc1394-13 but it is not going to be installed
       Depends: libdvbpsi4 but it is not going to be installed
       Depends: libdvdnav4 (>= 0.1.9) but it is not going to be installed
       Depends: libgsm1 (>= 1.0.10) but it is not going to be installed
       Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
       Depends: libiso9660-4 but it is not going to be installed
       Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not going to be installed       Depends: libmpeg2-4 but it is not going to be installed
       Depends: libtar but it is not going to be installed
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not going to be installed
       Depends: wxvlc but it is not going to be installed
       Depends: vlc-plugin-alsa but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


When i try the solution provided by apt-get I get the folloeing message....

specialist@specialist-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20.5) but 2.3.6.ds1-13 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



Please help me out......

---

