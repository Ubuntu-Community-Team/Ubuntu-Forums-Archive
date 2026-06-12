---
title: "apt-get install -f error (1)"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by rafaelcbf on 2011-10-16
I run apt-get install -f and I get this 


rafaelcbf@rafaelcbf-AOA150:~$ sudo apt-get install -f
[sudo] password for rafaelcbf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  liblash3 libpanel-applet-4-0 libboost-python1.46.1 libswscale0 python-opengl
  libbluray0 libswt-gnome-gtk-3.6-jni phonon python-gtkglext1 libpostproc51
  python-pypdf libwsutil0 libboost-thread1.42.0 libswt-gtk-3.6-java
  libavformat52 libdvbpsi6 virtualbox-ose-guest-utils
  libswt-webkit-gtk-3.6-jni libswt-cairo-gtk-3.6-jni libswt-gtk-3.6-jni
  python-rsvg libavfilter1 phonon-backend-gstreamer libmagick++3 libphonon4
  libcheese-gtk18 libwireshark0 python-pythonmagick virtualbox-ose-guest-dkms
  libquicktime1 libwiretap0 libgtkglext1 libglademm-2.4-1c2a freeglut3
  libmatroska3 gir1.2-panelapplet-4.0 libboost-python1.42.0 libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binutils
Suggested packages:
  binutils-doc
The following packages will be upgraded:
  binutils
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
8 not fully installed or removed.
Need to get 0 B/2,387 kB of archives.
After this operation, 1,090 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 224850 files and directories currently installed.)
Preparing to replace binutils 2.21.0.20110327-2ubuntu3 (using .../binutils_2.21.53.20110810-0ubuntu3_i386.deb) ...
Unpacking replacement binutils ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/binutils_2.21.53.20110810-0ubuntu3_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/man/man1/ld.bfd.1.gz'
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/binutils_2.21.53.20110810-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What can I do? I need to do it so I can use the Ubuntu Software Center.

---

### Post by rafaelcbf on 2011-10-16
Bump

---

