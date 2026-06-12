---
title: "Issues with full-upgrade"
date: 2008-06-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-06-06
Hi all, 
 Look at the following :-

shirish@Mugglewille:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  kcontrol kdebase-bin-kde4 kdebase-kde4 kdebase-runtime-data kicker kpat-kde4 libapt-pkg-perl libffi4 
  python-apt synaptic 
The following packages will be REMOVED:
  kdebase-data-kde4{a} 
The following packages will be upgraded:
  apt apt-utils aptitude cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base kdebase-data libept0 libstdc++6-4.2-dev 
The following packages are RECOMMENDED but will NOT be installed:
  aptitude-doc-cs aptitude-doc-en aptitude-doc-fi aptitude-doc-fr aptitude-doc-ja 
10 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 11.8MB of archives. After unpacking 15.7MB will be freed.
The following packages have unmet dependencies:
  kcontrol: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu1 is to be installed.
  kpat-kde4: Depends: kdebase-data-kde4 but it is not installable
  kdebase-bin-kde4: Depends: kdebase-data-kde4 (= 4:4.0.3-0ubuntu2) but it is not installable
  python-apt: Depends: libapt-inst-libc6.7-6-1.1 which is a virtual package.
              Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  kicker: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu1 is to be installed.
  libapt-pkg-perl: Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  libffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-0ubuntu2 is to be installed.
  kdebase-kde4: Depends: kdebase-data-kde4 (>= 4:4.0.3-0ubuntu2) but it is not installable
  synaptic: Depends: libapt-inst-libc6.7-6-1.1 which is a virtual package.
            Depends: libapt-pkg-libc6.7-6-4.6 which is a virtual package.
  kdebase-runtime-data: Depends: kdebase-runtime-data-common (>= 4:4.0.80-1ubuntu1) but it is not installable or
                                 kdebase-data (< 4:4.0.0-1) but 4:4.0.80-1ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
aptitude
tasksel
tasksel-data
ubuntu-minimal

Keep the following packages at their current version:
apt [0.7.14ubuntu2 (now)]
apt-utils [0.7.14ubuntu2 (now)]
cpp-4.2 [4.2.3-2ubuntu7 (now)]
g++-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2-base [4.2.3-2ubuntu7 (now)]
kdebase-data [4:3.5.9-0ubuntu7.2 (now)]
kdebase-data-kde4 [4:4.0.3-0ubuntu2 (intrepid, now)]
libept0 [0.5.17 (now)]
libstdc++6-4.2-dev [4.2.3-2ubuntu7 (now)]

Score is 594

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

I have queries such as why aptitude is being asked to be removed? The same with tasksel, ubuntu-minimal etc. which would be removed if I went with this solution/resolution. 

Comments and suggestions would be welcome on the same. For right now, I have quit the update/upgrade.

---

### Post by dinxter on 2008-06-07
during development the available packages and dependencies will repeatedly get out of synchronisation at times. i'd recommend using synaptic and updating packages 'by hand'. 
this way you can hold off upgrading a package that has dependency problems that cause a lot of other packages to be removed. then you can wait until the necessary upgrades reach the repositories before upgrading safely-ish :)

in this particular case there would be no severe breakage removing those four packages, unless you use aptitude a lot. it would probably be a good idea to reinstall them when the newer versions are available though

---

### Post by caryb on 2008-06-07
Wish I had read this before I hosed my system:confused:


Cary

---

### Post by dinxter on 2008-06-07
dodgy upgrades can sometimes be remidied by downgrading some packages by getting previous versions from [here]("http://archive.ubuntu.com/ubuntu/pool/"). Its a pain but it can usually be done unless something has gone very badly wrong!

---

### Post by Gina on 2008-06-09
I check whether there are any items held back before proceeding with an update and if there are I wait until there is a complete update available.  So far that has worked.

---

### Post by almostlinux on 2008-06-09
I usually stick with apt-get. aptitude has always led me into troubles.

---

