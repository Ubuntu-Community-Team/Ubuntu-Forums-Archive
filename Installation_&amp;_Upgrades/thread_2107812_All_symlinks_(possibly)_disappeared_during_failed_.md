---
title: "All symlinks (possibly?) disappeared during failed udate/upgrade"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by darkstormyrain on 2013-01-22
I'm using 13.04 Raring amd64 and this latest upgrade has me disturbed

it failed to configure a few packages somewhere down the link so as I was trying to manually resolve them and now nothing will launch via console or gui.

Here is exactly what happened from the point I discovered the failed upgrade to now.  Any ideas on how to solve this would be greatly apreciated.

darkrain@Rain:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apt-utils debconf debconf-i18n dpkg gcc-4.7-base libapt-inst1.5 libapt-pkg4.12 libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1 libstdc++6
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl perl-base tar zlib1g
Suggested packages:
  xz-utils debconf-doc debconf-utils whiptail dialog gnome-utils libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl libqtgui4-perl libqtcore4-perl apt bzip2 ncompress
The following NEW packages will be installed:
  apt-utils debconf debconf-i18n dpkg gcc-4.7-base libapt-inst1.5 libapt-pkg4.12 libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1 libstdc++6
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl perl-base tar zlib1g
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/6,559 kB of archives.
After this operation, 22.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libbz2-1.0_1.0.6-4_amd64.deb containing libbz2-1.0:amd64, pre-dependency problem:
 libbz2-1.0 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.

dpkg: error processing /var/cache/apt/archives/libbz2-1.0_1.0.6-4_amd64.deb (--unpack):
 pre-dependency problem - not installing libbz2-1.0:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libbz2-1.0_1.0.6-4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
darkrain@Rain:~$ sudo sudo apt-get install -fdpkg --configure -a
[sudo] password for darkrain: 
E: Command line option 'p' [from -fdpkg] is not known.
darkrain@Rain:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6:amd64:
 libc6:amd64 depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not installed.
  Package debconf-2.0 is not installed.
 libc6:amd64 depends on libgcc1; however:
  Package libgcc1 is not installed.

dpkg: error processing libc6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6:amd64 is not configured yet.

dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6:amd64
 multiarch-support
darkrain@Rain:~$ sudo aptitude -f -y --full-resolver upgrade
The following partially installed packages will be configured:
  libc6{b} multiarch-support 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
 libc6 : Depends: debconf (>= 0.5) but it is not going to be installed. or
                  debconf-2.0 which is a virtual package.
         Depends: libgcc1 but it is not going to be installed.
open: 6; closed: 127; defer: 3; conflict: 4                                                                                                                                 .The following actions will resolve these dependencies:

     Remove the following packages:
1)     libc6                       
2)     multiarch-support           



The following packages will be REMOVED:
  libc6{a} multiarch-support{a} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 10.8 MB will be freed.
(Reading database ... 471 files and directories currently installed.)
Removing multiarch-support ...
Removing libc6:amd64 ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/libc6:amd64.postrm): No such file or directory
dpkg: error processing libc6:amd64 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libc6:amd64
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
Current status: 23090 new [+23015].
darkrain@Rain:~$ sudo -s
bash: /usr/bin/sudo: No such file or directory
darkrain@Rain:~$ sudo
bash: /usr/bin/sudo: No such file or directory
darkrain@Rain:~$ gksu
bash: /usr/bin/gksu: No such file or directory
darkrain@Rain:~$ aptitude
bash: /usr/bin/aptitude: No such file or directory
darkrain@Rain:~$ find . -name aptitude
bash: /usr/bin/find: No such file or directory
darkrain@Rain:~$ ls /usr/bin
bash: /bin/ls: No such file or directory

---

### Post by matt_symes on 2013-01-22
Hi

You cannot run anything because libc is not installed correctly on your system.

You are aware of course that ringtail is in development and, so, i am sure the machine you are running it on is a test machine.

As it is a test machine, my advice is to reinstall. A lot less of a headache than trying to fix your dependency issues in the long run and reinstalling libc could be a pain.

Kind regards

---

### Post by darkstormyrain on 2013-02-08
Thanks for your input,   I ended up mounting a btrfs 2 week old subvolume to restore my system but also took the oprotunity to learn more.  

Compiled a  static sets of tools (coreutils, bash etc..) the bare minimum to work with installed them on the bad volume spent part of the day  learning a bit more about the file system.

---

