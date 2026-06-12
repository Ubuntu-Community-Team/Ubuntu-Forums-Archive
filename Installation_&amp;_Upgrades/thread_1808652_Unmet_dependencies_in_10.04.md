---
title: "Unmet dependencies in 10.04 ?"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by cparry on 2011-07-20
Folks,

I'm trying to perform a "sudo apt-get install build-essential"
on Ubunbtu 10.04 LTS (updated to linux-headers-2.6.32-33)
however it reports ...

----------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages
----------------------------

Now I have done a "sudo apt-cache show g++" which reports ...

----------------------------
Package: g++
Priority: optional
Section: devel
Installed-Size: 40
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: i386
Source: gcc-defaults (1.93ubuntu2)
Version: 4:4.4.4-1ubuntu2
Provides: c++-compiler
Depends: cpp (>= 4:4.4.4-1ubuntu2), gcc (>= 4:4.4.4-1ubuntu2), g++-4.4 (>= 4.4.4-1), gcc-4.4 (>= 4.4.4-1)
Suggests: g++-multilib
Filename: pool/main/g/gcc-defaults/g++_4.4.4-1ubuntu2_i386.deb
Size: 1444
MD5Sum: 4e3190bd7e336e9640cc643118e43a2b
SHA1: 00b93d0f004b9d22869cada9c518b23a7bb035ef
SHA256: c19b0f7802bbd3bed06ed469b4b51b33b2bb7900a54fd27f4404f31a602b77c2
Description: The GNU C++ compiler
 This is the GNU C++ compiler, a fairly portable optimizing compiler for C++.
 .
 This is a dependency package providing the default GNU C++ compiler.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Build-Essential: yes
Origin: Ubuntu
Supported: 18m

Package: g++
Priority: optional
Section: devel
Installed-Size: 40
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: i386
Source: gcc-defaults (1.93ubuntu1)
Version: 4:4.4.3-1ubuntu1
Provides: c++-compiler
Depends: cpp (>= 4:4.4.3-1ubuntu1), gcc (>= 4:4.4.3-1ubuntu1), g++-4.4 (>= 4.4.3-1), gcc-4.4 (>= 4.4.3-1)
Suggests: g++-multilib
Filename: pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb
Size: 1442
MD5sum: 6870e35924098271b118b05419aa6aa2
SHA1: 3e0aa1439812d101bdcaa2b95e5cca82b65a7ee2
SHA256: 8f1bbe5fe0acc10fc363bf3fe64d38273d4e64a8196ed4e4287de5b0e09b7bfc
Description: The GNU C++ compiler
 This is the GNU C++ compiler, a fairly portable optimizing compiler for C++.
 .
 This is a dependency package providing the default GNU C++ compiler.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Build-Essential: yes
Origin: Ubuntu
Supported: 5y
----------------------------

Similarily, the "sudo apt-cache show dpkg-dev" is reporting Version: 1.15.8.4ubuntu3
(also Version: 1.15.5.6ubuntu4.5, and Version: 1.15.5.6ubuntu4 ?)

Now if I'm reading these correctly, build-essential ...
o wants g++ >= 4:4.4.3, but I already have 4:4.4.4-1ubuntu2 ?
o wants dpkg-dev >= 1.13.5, but I already have 1.15.8.4ubuntu3 ?

Suggestions, please ?

---

### Post by zvacet on 2011-07-20
```
sudo apt-get -f install
```

---

### Post by cparry on 2011-07-20
Ok ... but all that gives me is ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

---

### Post by zvacet on 2011-07-20
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cparry on 2011-07-26
Ok but essentially no change ... it gave me ...

----------------------------
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils base-files evolution-common hpijs hplip
  hplip-data libhpmud0 libimobiledevice0 libparted0debian1 openssh-client
  parted python-apt ssh-askpass-gnome
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Fetched 19.4MB in 15s (1,278kB/s)                                              
(Reading database ... 281615 files and directories currently installed.)
Preparing to replace base-files 5.0.0ubuntu20.10.04.3 (using .../base-files_5.0.0ubuntu20.10.04.4_i386.deb) ...
Unpacking replacement base-files ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up base-files (5.0.0ubuntu20.10.04.4) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...

(Reading database ... 281615 files and directories currently installed.)
Preparing to replace hpijs 3.10.2-2ubuntu2 (using .../hpijs_3.10.2-2ubuntu2.2_i386.deb) ...
Unpacking replacement hpijs ...
Preparing to replace hplip 3.10.2-2ubuntu2 (using .../hplip_3.10.2-2ubuntu2.2_i386.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.10.2-2ubuntu2 (using .../libhpmud0_3.10.2-2ubuntu2.2_i386.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.10.2-2ubuntu2 (using .../hplip-data_3.10.2-2ubuntu2.2_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace apt 0.7.25.3ubuntu9.5 (using .../apt_0.7.25.3ubuntu9.6_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.7.25.3ubuntu9.6) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 281615 files and directories currently installed.)
Preparing to replace apt-utils 0.7.25.3ubuntu9.5 (using .../apt-utils_0.7.25.3ubuntu9.6_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace apt-transport-https 0.7.25.3ubuntu9.5 (using .../apt-transport-https_0.7.25.3ubuntu9.6_i386.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace openssh-client 1:5.3p1-3ubuntu6 (using .../openssh-client_1%3a5.3p1-3ubuntu7_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace libparted0debian1 2.2-5ubuntu5.1 (using .../libparted0debian1_2.2-5ubuntu5.2_i386.deb) ...
Unpacking replacement libparted0debian1 ...
Preparing to replace parted 2.2-5ubuntu5.1 (using .../parted_2.2-5ubuntu5.2_i386.deb) ...
Unpacking replacement parted ...
Preparing to replace python-apt 0.7.94.2ubuntu6.2 (using .../python-apt_0.7.94.2ubuntu6.4_i386.deb) ...
Unpacking replacement python-apt ...
Preparing to replace evolution-common 2.28.3-0ubuntu10.2 (using .../evolution-common_2.28.3-0ubuntu10.3_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace libimobiledevice0 0.9.7-1ubuntu1 (using .../libimobiledevice0_0.9.7-1ubuntu1.1_i386.deb) ...
Unpacking replacement libimobiledevice0 ...
Preparing to replace ssh-askpass-gnome 1:5.3p1-3ubuntu6 (using .../ssh-askpass-gnome_1%3a5.3p1-3ubuntu7_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Processing triggers for python-support ...
Setting up libhpmud0 (3.10.2-2ubuntu2.2) ...

Setting up hpijs (3.10.2-2ubuntu2.2) ...

Setting up hplip-data (3.10.2-2ubuntu2.2) ...

Setting up hplip (3.10.2-2ubuntu2.2) ...
Creating/updating hplip user account...

Setting up apt-utils (0.7.25.3ubuntu9.6) ...

Setting up apt-transport-https (0.7.25.3ubuntu9.6) ...
Setting up openssh-client (1:5.3p1-3ubuntu7) ...

Setting up libparted0debian1 (2.2-5ubuntu5.2) ...

Setting up parted (2.2-5ubuntu5.2) ...
Setting up python-apt (0.7.94.2ubuntu6.4) ...

Setting up evolution-common (2.28.3-0ubuntu10.3) ...
Setting up libimobiledevice0 (0.9.7-1ubuntu1.1) ...

Setting up ssh-askpass-gnome (1:5.3p1-3ubuntu7) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...
----------------------------

and a "sudo apt-get install build-essential" still reports

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

Thanks,

---

### Post by ajlckwd on 2011-07-26
having the same issue... anyone have any ideas on how to fix or how the dependencies are breaking in the first place?

---

