---
title: "[DEBCONF] need a fix for sceptically broken debconf"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by hd.scania on 2016-10-11
```
hd_scania@HD-SCANIA:~$ su
Password: 
root@HD-SCANIA:/home/hd_scania# apt upgrade perl-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  dpkg gcc-6-base libacl1 libattr1 libbz2-1.0 libc6 libgcc1 liblzma5 libpcre3 libselinux1 multiarch-support perl-base tar zlib1g
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,683 kB of archives.
After this operation, 28.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
root@HD-SCANIA:/home/hd_scania# apt-extracttemplates
apt 1.2.14 (amd64)
Usage: apt-extracttemplates file1 [file2 ...]


apt-extracttemplates is used to extract config and template files
from debian packages. It is used mainly by debconf(1) to prompt for
configuration questions before installation of packages.


See apt-extracttemplates(1) for more information about the available commands.
Configuration options and syntax is detailed in apt.conf(5).
Information about how to configure sources can be found in sources.list(5).
Package and version choices can be expressed via apt_preferences(5).
Security details are available in apt-secure(8).
root@HD-SCANIA:/home/hd_scania# apt-extracttemplates /var/cache/apt/archives/debconf_1.5.58ubuntu1_all.deb
E: Cannot get debconf version. Is debconf installed?
root@HD-SCANIA:/home/hd_scania# apt-extracttemplates /var/cache/apt/archives/perl-base_5.22.1-9_amd64.deb
E: Cannot get debconf version. Is debconf installed?
root@HD-SCANIA:/home/hd_scania# exit
exit
hd_scania@HD-SCANIA:~$ su
Password: 
root@HD-SCANIA:/home/hd_scania# apt update && apt clean && apt install -fy && dpkg -i /var/cache/apt/archives/*.deb && dpkg --configure -a && apt install -fy && apt dist-upgrade && exit
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease                                                     
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                       
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                                             
...
Get:49 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse DEP-11 64x64 Icons [2,699 B]                                              
Fetched 3,105 kB in 56s (54.9 kB/s)                                                                                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bash bash-completion bsdmainutils bsdutils coreutils dash dbus debconf debconf-i18n
  debianutils diffutils dmsetup dpkg e2fslibs e2fsprogs findutils gcc-5-base gcc-6-base gnupg gpgv grep gzip hostname init
  init-system-helpers libacl1 libapparmor1 libapt-inst2.0 libapt-pkg5.0 libattr1 libaudit-common libaudit1 libblkid1 libbz2-1.0 libc-bin
  libc6 libcap-ng0 libcap2 libcap2-bin libcomerr2 libcryptsetup4 libdb5.3 libdbus-1-3 libdebconfclient0 libdevmapper1.02.1 libexpat1
  libfdisk1 libgcc1 libgcrypt20 libgpg-error0 libgpm2 libkmod2 liblocale-gettext-perl liblz4-1 liblzma5 libmount1 libncursesw5 libpam-cap
  libpam-modules libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpcre3 libreadline6 libseccomp2 libselinux1 libsemanage-common
  libsemanage1 libsepol1 libsmartcols1 libss2 libstdc++6 libsystemd0 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libtinfo5 libudev1 libusb-0.1-4 libustr-1.0-1 libuuid1 login lsb-base mawk mount multiarch-support ncurses-base ncurses-bin passwd
  perl-base readline-common sed sensible-utils systemd systemd-sysv sysvinit-utils tar ubuntu-keyring update-motd util-linux uuid-runtime
  zlib1g
0 upgraded, 108 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.4 MB of archives.
After this operation, 104 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 gcc-6-base amd64 6.0.1-0ubuntu1 [14.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libc6 amd64 2.23-0ubuntu3 [2,584 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgcc1 amd64 1:6.0.1-0ubuntu1 [38.5 kB]
...
Get:108 http://archive.ubuntu.com/ubuntu xenial/main amd64 update-motd all 3.6-0ubuntu1 [5,378 B]                                            
Fetched 25.4 MB in 7min 2s (60.1 kB/s)                                                                                                       
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 27%
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 55%
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 83%
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
exit
hd_scania@HD-SCANIA:~$ su
Password: 
root@HD-SCANIA:/home/hd_scania# ls -l /var/cache/apt/archives
total 4
-rwxrwxr-- 1 root root    0 Oct  9 19:39 lock
drwx------ 2 _apt root 4096 Oct 11 19:49 partial
root@HD-SCANIA:/home/hd_scania# ls -l /var/cache/apt/archives/partial
total 0
root@HD-SCANIA:/home/hd_scania# cd /var/cache/apt/archives
root@HD-SCANIA:/var/cache/apt/archives# chmod 775 ./ ../ ./* && chown root:root ./ ../ ./* && ls -la
total 80
drwxrwxr-x 3 root root 69632 Oct 11 20:29 .
drwxrwxr-x 3 root root  4096 Oct 11 20:29 ..
-rwxrwxr-x 1 root root     0 Oct  9 19:39 lock
drwxrwxr-x 2 root root  4096 Oct 11 20:29 partial
root@HD-SCANIA:/var/cache/apt/archives# dpkg --force-depends -i dpkg_1.14.16.6ubuntu4_i386.deb
root@HD-SCANIA:/var/cache/apt/archives# dpkg --force-depends -i debconf_1.5.20_all.deb
root@HD-SCANIA:/var/cache/apt/archives# dpkg --force-depends -i apt_0.7.9ubuntu17.2_i386.deb
root@HD-SCANIA:/var/cache/apt/archives# dpkg --force-depends -i apt-utils_0.7.9ubuntu17.2_i386.deb
root@HD-SCANIA:/var/cache/apt/archives# ls -la
total 80
drwxrwxr-x 3 root root 69632 Oct 11 19:49 .
drwxrwxr-x 3 root root  4096 Oct 11 19:49 ..
-rwxrwxr-x 1 root root     0 Oct  9 19:39 lock
drwxrwxr-x 2 _apt root  4096 Oct 11 19:49 partial
root@HD-SCANIA:/var/cache/apt/archives# apt update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                            
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease                                                                          
Hit:5 http://ppa.launchpad.net/atareao/telegram/ubuntu xenial InRelease                                                       
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]                                                     
Hit:7 http://ppa.launchpad.net/rodsmith/refind/ubuntu xenial InRelease                                    
Hit:8 http://archive.canonical.com/ubuntu xenial InRelease                                                 
Hit:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease                              
Get:10 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Fetched 437 kB in 7s (55.5 kB/s)                                                                                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@HD-SCANIA:/var/cache/apt/archives# dpkg -l | grep ii
root@HD-SCANIA:/var/cache/apt/archives# dpkg -l | grep ii | awk '{print "apt-get --reinstall -y install", $2}' > /tmp/reinstall && sh /tmp/reinstall
root@HD-SCANIA:/var/cache/apt/archives# apt install --reinstall ucf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adduser apt apt-utils coreutils debconf debconf-i18n debianutils dpkg gcc-5-base gcc-6-base gnupg gpgv init-system-helpers libacl1
  libapt-inst2.0 libapt-pkg5.0 libattr1 libaudit-common libaudit1 libbz2-1.0 libc6 libdb5.3 libgcc1 liblocale-gettext-perl liblz4-1 liblzma5
  libpam-modules libpam-modules-bin libpam0g libpcre3 libreadline6 libselinux1 libsemanage-common libsemanage1 libsepol1 libstdc++6
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtinfo5 libusb-0.1-4 libustr-1.0-1 lsb-base multiarch-support passwd
  perl-base readline-common sensible-utils tar ubuntu-keyring update-motd zlib1g
Suggested packages:
  perl-modules ecryptfs-utils aptitude | synaptic | wajig dpkg-dev apt-doc python-apt debconf-doc debconf-utils whiptail | dialog
  libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl perl libqtgui4-perl libqtcore4-perl gnupg-curl gnupg-doc libpcsclite1 parcimonie
  xloadimage | imagemagick | eog glibc-doc locales libpam-doc readline-doc bzip2 ncompress xz-utils tar-scripts
The following NEW packages will be installed:
  adduser apt apt-utils coreutils debconf debconf-i18n debianutils dpkg gcc-5-base gcc-6-base gnupg gpgv init-system-helpers libacl1
  libapt-inst2.0 libapt-pkg5.0 libattr1 libaudit-common libaudit1 libbz2-1.0 libc6 libdb5.3 libgcc1 liblocale-gettext-perl liblz4-1 liblzma5
  libpam-modules libpam-modules-bin libpam0g libpcre3 libreadline6 libselinux1 libsemanage-common libsemanage1 libsepol1 libstdc++6
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtinfo5 libusb-0.1-4 libustr-1.0-1 lsb-base multiarch-support passwd
  perl-base readline-common sensible-utils tar ubuntu-keyring ucf update-motd zlib1g
0 upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3 MB of archives.
After this operation, 57.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 gcc-6-base amd64 6.0.1-0ubuntu1 [14.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libc6 amd64 2.23-0ubuntu3 [2,584 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgcc1 amd64 1:6.0.1-0ubuntu1 [38.5 kB]
...                                                           
Get:53 http://archive.ubuntu.com/ubuntu xenial/main amd64 update-motd all 3.6-0ubuntu1 [5,378 B]                                             
Fetched 14.3 MB in 7min 34s (31.4 kB/s)                                                                                                      
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 56%
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
root@HD-SCANIA:/var/cache/apt/archives# exit
exit
hd_scania@HD-SCANIA:~$
```
I have just followed the online examples from 2015 and nothing are done.

---

