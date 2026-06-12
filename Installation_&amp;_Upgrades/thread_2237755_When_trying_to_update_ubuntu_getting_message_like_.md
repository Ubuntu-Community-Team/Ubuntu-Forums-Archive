---
title: "When trying to update ubuntu getting message like &quot;The Package System is broken&quot;"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by avinash5 on 2014-08-03
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:


default-jdk: Depends: default-jre (= 1:1.6-43ubuntu2) but 1:1.6-43ubuntu2 is installed
             Depends: openjdk-6-jdk (>= 6b23~pre11-1ubuntu1~) but it is not installed
eclipse-platform: Depends: eclipse-platform-data (>= 3.7.2-1) but 3.7.2-1 is installed
                  Depends: eclipse-rcp (= 3.7.2-1) but 3.7.2-1 is installed
                  Depends: libjasper-java (>= 5.5.26) but 5.5.33-2 is installed
                  Depends: libjetty-java (>= 6.1.24-4~) but it is not installed
                  Depends: liblucene2-java (< 2.9.5) but 2.9.4+ds1-4 is installed
                  Depends: libservlet2.5-java (>= 6.0.20-8) but 6.0.35-1ubuntu3.4 is installed
                  Depends: sat4j (< 2.4.0) but 2.3.1-1 is installed
libswt-webkit-gtk-3-jni: Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not installed


Even i'm not able to install any software from "ubuntu software center" getting message like "Item cannot be installed or Remove until the package catalog is repaired.Do you want to repair it now?"
Even after clicking repair i'm getting  message like "Package Operation Failed"

---

### Post by avinash5 on 2014-08-03
I tried running "sudo apt-get install -f" also getting output as below:-

sudo apt-get install -f
[sudo] password for avinash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mingw-w64 sbsigntool libcogl9 gir1.2-timezonemap-1.0 gnome-js-common
  realpath efibootmgr libcogl-pango0 diffstat libdmraid1.0.0.rc16
  libdebconfclient0 binutils-mingw-w64-i686 kpartx-boot libopts25
  gir1.2-json-1.0 quilt autogen gcc-mingw-w64 user-setup gcc-mingw-w64-i686
  kpartx rdate gir1.2-coglpango-1.0 libclutter-1.0-common
  binutils-mingw-w64-x86-64 libdebian-installer4 libopts25-dev
  libclutter-1.0-0 btrfs-tools apt-clone localechooser-data gcc-mingw-w64-base
  gcc-mingw-w64-x86-64 archdetect-deb dmraid python-pyicu libseed-gtk3-0
  mingw-w64-dev libcogl-common gir1.2-xkl-1.0 gir1.2-cogl-1.0
  gir1.2-clutter-1.0 epiphany-browser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjetty-java libwebkitgtk-1.0-0 openjdk-6-jdk
Suggested packages:
  jetty libjetty-java-doc openjdk-6-demo openjdk-6-source visualvm
The following NEW packages will be installed:
  libjetty-java libwebkitgtk-1.0-0 openjdk-6-jdk
0 upgraded, 3 newly installed, 0 to remove and 444 not upgraded.
6 not fully installed or removed.
Need to get 0 B/23.8 MB of archives.
After this operation, 45.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/openjdk-6-jdk_6b31-1.13.3-1ubuntu1~0.12.04.2_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libwebkitgtk-1.0-0_1.8.3-0ubuntu0.12.04.1_amd64.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libjetty-java_6.1.24-6ubuntu0.12.04.1_all.deb
debconf: apt-extracttemplates failed: No such file or directory
dpkg-deb: error: `/var/cache/apt/archives/openjdk-6-jdk_6b31-1.13.3-1ubuntu1~0.12.04.2_amd64.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/openjdk-6-jdk_6b31-1.13.3-1ubuntu1~0.12.04.2_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
(Reading database ... 157749 files and directories currently installed.)
Unpacking libwebkitgtk-1.0-0 (from .../libwebkitgtk-1.0-0_1.8.3-0ubuntu0.12.04.1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid distance code'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libwebkitgtk-1.0-0_1.8.3-0ubuntu0.12.04.1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libwebkitgtk-1.0.so.0.13.4'
dpkg-deb: error: `/var/cache/apt/archives/libjetty-java_6.1.24-6ubuntu0.12.04.1_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libjetty-java_6.1.24-6ubuntu0.12.04.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jdk_6b31-1.13.3-1ubuntu1~0.12.04.2_amd64.deb
 /var/cache/apt/archives/libwebkitgtk-1.0-0_1.8.3-0ubuntu0.12.04.1_amd64.deb
 /var/cache/apt/archives/libjetty-java_6.1.24-6ubuntu0.12.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by avinash5 on 2014-08-03
[COLOR=#333333][FONT=UbuntuRegular]I've tried everything people recommend on internet like:[/FONT][/COLOR]
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
[COLOR=#000000]sudo apt-get remove --purge
but nothing is working for me.
I'm using ubuntu 12.0.4 64bits
Any suggestions or help is appreciated.

[/COLOR]

---

