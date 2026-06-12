---
title: "Many errors installing packages during upgrading to 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by yang on 2008-04-25
I ran into a bunch of problems upgrading from 7.10 to 8.04. During the "Installing the ugprades" part of the setup procedure, I got a ton of errors.

The very first one was titled "Could not install 'libdb4.6'" and had the detailed message "no package named `libdb4.6' is installed, cannot configure".

Then what followed were a number of error dialogs for other packages that popped up afterward, all with the detailed message "dependency problems - leaving unconfigured." I'm guessing they were dependent on libdb4.6's successful installation. These were the packages:

- libpam-modules
- login
- passwd
- libuuid1
- e2fsprogs
- python2.5
- python

Then I saw "Could not install '/var/cache/apt/archives/xserver-xorg_1%3a7.3+10ubuntu10_all.deb'" with the detailed message "pre-dependency problem - not installing xserver-xorg."

Then I saw a stream of other errors:

- package perl-modules is already installed and configured
- package libnewt0.52 is already installed and configured
- package whiptail is already installed and configured
- package defoma is already installed and configured
- package gsfonts is already installed and configured
- package ttf-dejavu-extra is already installed and configured
- package ttf-dejavu is already installed and configured
- package ucf is already installed and configured
- package fontconfig-config is already installed and configured
- package libexpat1 is already installed and configured
- package libfontconfig1 is already installed and configured

Then some more of the "dependency problems - leaving unconfigured":

- libsasl2-2
- libldap-2.4-2
- ssl-cert
- cupsys
- libsasl2-modules

For some time, I haven't seen any errors, so I'm submitting this for now.

---

### Post by yang on 2008-04-25
Crap.

I just got another one: "package libice6 is already installed and configured."

And finally I see:

```
Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed
```

AAAaarggh!

---

### Post by yang on 2008-04-28
Anybody?

Now after rebooting, I'm seeing:

```

yang@harvard ~
$ sudo apt-get dist-upgrade
[sudo] password for yang:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

yang@harvard ~
$ sudo dpkg --configure -a
Setting up libgmpxx4ldbl (2:4.2.2+dfsg-1ubuntu2) ...

Setting up libdjvulibre15 (3.5.20-2) ...

Setting up librpcsecgss3 (0.17-1ubuntu1) ...

Setting up upstart-logd (0.3.9-2) ...
Setting up libflac8 (1.2.1-1ubuntu2) ...

Setting up man-db (2.5.1-3) ...
Installing new version of config file /etc/manpath.config ...
Installing new version of config file /etc/cron.daily/man-db ...
Installing new version of config file /etc/cron.weekly/man-db ...
scrollkeeper-update: deferring update until scrollkeeper is configured

Setting up libesd-alsa0 (0.2.38-0ubuntu9) ...

Setting up pulseaudio-utils (0.9.10-1ubuntu1) ...
Setting up libpisync1 (0.12.3-4ubuntu1) ...

Setting up libsdl1.2debian (1.2.13-1ubuntu1) ...
Setting up tk8.4 (8.4.16-2ubuntu1) ...

Setting up libopenssl-ruby1.8 (1.8.6.111-2ubuntu1) ...
Setting up cpp-4.1 (4.1.2-21ubuntu1) ...
Setting up whois (4.7.24) ...
Setting up wamerican (6-2.1) ...

dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on x11-session-utils; however:
  Package x11-session-utils is not installed.
 xbase-clients depends on x11-utils; however:
  Package x11-utils is not installed.
 xbase-clients depends on x11-xfs-utils; however:
  Package x11-xfs-utils is not installed.
dpkg: error processing xbase-clients (--configure):
 dependency problems - leaving unconfigured
Setting up dvd+rw-tools (7.0-9ubuntu1) ...
Setting up libqt3-mt (3:3.3.8-b-0ubuntu3) ...

Setting up libuniconf4.4 (4.4.1-0ubuntu2) ...

Setting up libnm-util0 (0.6.6-0ubuntu5) ...

Setting up libltdl3-dev (1.5.26-1ubuntu1) ...
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on x11-session-utils; however:
  Package x11-session-utils is not installed.
 xorg depends on x11-utils; however:
  Package x11-utils is not installed.
 xorg depends on x11-xfs-utils; however:
  Package x11-xfs-utils is not installed.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
Setting up libgda3-3 (3.0.2-2ubuntu1) ...

Setting up libmysqlclient15off (5.0.51a-3ubuntu5) ...

dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev (>= 2.5.0-2ubuntu2); however:
  Version of libfontconfig1-dev on system is 2.4.2-1.2ubuntu4.
dpkg: error processing libcairo2-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libungif4g (4.1.6-4) ...
Setting up mono-jit (1.2.6+dfsg-6ubuntu3) ...

Setting up libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) ...

dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libcairo2-dev (>= 1.2.6); however:
  Package libcairo2-dev is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
Setting up manpages-dev (2.77-1) ...
Setting up lapack3 (3.0.20000531a-6.1ubuntu1) ...

dpkg: dependency problems prevent configuration of libpam-modules:
 libpam-modules depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libpam-modules (--configure):
 dependency problems - leaving unconfigured
Setting up iftop (0.17-5) ...
Setting up myspell-en-gb (1:2.4.0~m240-1ubuntu1) ...
Updating OpenOffice.org's dictionary list... done.

dpkg: dependency problems prevent configuration of libpurple0:
 libpurple0 depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing libpurple0 (--configure):
 dependency problems - leaving unconfigured
Setting up libgd2-xpm-dev (2.0.35.dfsg-3ubuntu2) ...
Setting up libhal-storage1 (0.5.11~rc2-1ubuntu7) ...

Setting up libgstreamer-plugins-base0.10-0 (0.10.18-3) ...

Setting up linux-restricted-modules-common (2.6.24.12-16.34) ...

dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-extra:
 compiz-fusion-plugins-extra depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-fusion-plugins-extra (--configure):
 dependency problems - leaving unconfigured
Setting up libgsf-1-114 (1.14.7-2ubuntu1) ...

dpkg: dependency problems prevent configuration of gcc-4.2:
 gcc-4.2 depends on cpp-4.2 (= 4.2.3-2ubuntu7); however:
  Package cpp-4.2 is not installed.
dpkg: error processing gcc-4.2 (--configure):
 dependency problems - leaving unconfigured
Setting up libsdl-image1.2 (1.2.6-3) ...

Setting up freeglut3 (2.4.0-6) ...

dpkg: dependency problems prevent configuration of libapt-pkg-perl:
 libapt-pkg-perl depends on perl-base (>= 5.8.8-12); however:
  Version of perl-base on system is 5.8.8-7ubuntu3.1.
dpkg: error processing libapt-pkg-perl (--configure):
 dependency problems - leaving unconfigured
Setting up libbonobo2-0 (2.22.0-0ubuntu1) ...

dpkg: dependency problems prevent configuration of libsvn1:
 libsvn1 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libsvn1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dia-libs:
 dia-libs depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing dia-libs (--configure):
 dependency problems - leaving unconfigured
Setting up libpulsecore5 (0.9.10-1ubuntu1) ...

dpkg: dependency problems prevent configuration of grub:
 grub depends on debconf (>= 1.5.19) | cdebconf; however:
  Version of debconf on system is 1.5.14ubuntu1.
  Package cdebconf is not installed.
 grub depends on ucf (>= 3.004-0ubuntu2); however:
  Version of ucf on system is 3.001.
dpkg: error processing grub (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of base-files:
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not configured yet.
dpkg: error processing base-files (--configure):
 dependency problems - leaving unconfigured
Setting up bluez-audio (3.26-0ubuntu6) ...
Setting up libavahi-qt3-1 (0.6.22-2ubuntu4) ...

dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim:
 vim depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing vim (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-core:
 compiz-core depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iproute:
 iproute depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing iproute (--configure):
 dependency problems - leaving unconfigured
Setting up gstreamer0.10-plugins-ugly (0.10.7-3) ...
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
Setting up libreadline-ruby1.8 (1.8.6.111-2ubuntu1) ...
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xinit:
 xinit depends on xrdb; however:
  Package xrdb is not installed.
dpkg: error processing xinit (--configure):
 dependency problems - leaving unconfigured
Setting up gstreamer0.10-esd (0.10.7-3) ...
Setting up libsnmp15 (5.4.1~dfsg-4ubuntu4) ...

Setting up scim-modules-socket (1.4.7-3ubuntu8) ...
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up libgmp3-dev (2:4.2.2+dfsg-1ubuntu2) ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on cpp (>= 4:4.2.3-1ubuntu3); however:
  Version of cpp on system is 4:4.1.2-9ubuntu2.
 g++ depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of perl-tk:
 perl-tk depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing perl-tk (--configure):
 dependency problems - leaving unconfigured
Setting up libgcj8-1 (4.2.3-2ubuntu6) ...

dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on libpam-modules; however:
  Package libpam-modules is not configured yet.
dpkg: error processing samba-common (--configure):
 dependency problems - leaving unconfigured
Setting up startup-tasks (0.3.9-2) ...
dpkg: dependency problems prevent configuration of libaprutil1:
 libaprutil1 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libaprutil1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libcairo2-dev; however:
  Package libcairo2-dev is not configured yet.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserver1.2-9:
 libedataserver1.2-9 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libedataserver1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
Setting up libcwidget3 (0.5.8-1ubuntu1) ...

dpkg: dependency problems prevent configuration of libsasl2-2:
 libsasl2-2 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libsasl2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of passwd:
 passwd depends on libpam-modules (>= 0.72-5); however:
  Package libpam-modules is not configured yet.
dpkg: error processing passwd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-exchange depends on libdb4.6; however:
  Package libdb4.6 is not installed.
 evolution-exchange depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-file:
 apt-file depends on libapt-pkg-perl; however:
  Package libapt-pkg-perl is not configured yet.
dpkg: error processing apt-file (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex:
 openoffice.org-writer2latex depends on openoffice.org-core (>= 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer2latex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on passwd; however:
  Package passwd is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-main:
 compiz-fusion-plugins-main depends on compiz-core; however:
  Package compiz-core is not configured yet.
 compiz-fusion-plugins-main depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-fusion-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-utils:
 apache2-utils depends on libaprutil1; however:
  Package libaprutil1 is not configured yet.
dpkg: error processing apache2-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-compizconfig:
 python-compizconfig depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing python-compizconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-2.6.24-16-generic:
 linux-image-2.6.24-16-generic depends on module-init-tools (>= 3.3-pre11-4ubuntu3); however:
  Version of module-init-tools on system is 3.3-pre4-2ubuntu4.
dpkg: error processing linux-image-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on libpam-modules (>= 0.72-9); however:
  Package libpam-modules is not configured yet.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-mdns:
 libnss-mdns depends on base-files (>= 3.1.10); however:
  Package base-files is not configured yet.
dpkg: error processing libnss-mdns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-plugins depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xutils:
 xutils depends on xcursorgen; however:
  Package xcursorgen is not installed.
 xutils depends on sessreg; however:
  Package sessreg is not installed.
dpkg: error processing xutils (--configure):
 dependency problems - leaving unconfigured
Setting up aptitude (0.4.9-2ubuntu5) ...

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on smbclient; however:
  Package smbclient is not configured yet.
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-ttcidfont-conf:
 x-ttcidfont-conf depends on xutils; however:
  Package xutils is not configured yet.
dpkg: error processing x-ttcidfont-conf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libpurple0 (>= 1:2.4.1-1ubuntu2); however:
  Package libpurple0 is not configured yet.
 pidgin depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

yang@harvard ~
$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

yang@harvard ~
$ sudo dpkg --configure -a
Setting up gij-4.2 (4.2.3-2ubuntu6) ...

Setting up pulseaudio-module-x11 (0.9.10-1ubuntu1) ...
dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on x11-session-utils; however:
  Package x11-session-utils is not installed.
 xbase-clients depends on x11-utils; however:
  Package x11-utils is not installed.
 xbase-clients depends on x11-xfs-utils; however:
  Package x11-xfs-utils is not installed.
dpkg: error processing xbase-clients (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on x11-session-utils; however:
  Package x11-session-utils is not installed.
 xorg depends on x11-utils; however:
  Package x11-utils is not installed.
 xorg depends on x11-xfs-utils; however:
  Package x11-xfs-utils is not installed.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev (>= 2.5.0-2ubuntu2); however:
  Version of libfontconfig1-dev on system is 2.4.2-1.2ubuntu4.
dpkg: error processing libcairo2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libcairo2-dev (>= 1.2.6); however:
  Package libcairo2-dev is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-modules:
 libpam-modules depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libpam-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpurple0:
 libpurple0 depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing libpurple0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-extra:
 compiz-fusion-plugins-extra depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-fusion-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-4.2:
 gcc-4.2 depends on cpp-4.2 (= 4.2.3-2ubuntu7); however:
  Package cpp-4.2 is not installed.
dpkg: error processing gcc-4.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapt-pkg-perl:
 libapt-pkg-perl depends on perl-base (>= 5.8.8-12); however:
  Version of perl-base on system is 5.8.8-7ubuntu3.1.
dpkg: error processing libapt-pkg-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsvn1:
 libsvn1 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libsvn1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dia-libs:
 dia-libs depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing dia-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub:
 grub depends on debconf (>= 1.5.19) | cdebconf; however:
  Version of debconf on system is 1.5.14ubuntu1.
  Package cdebconf is not installed.
 grub depends on ucf (>= 3.004-0ubuntu2); however:
  Version of ucf on system is 3.001.
dpkg: error processing grub (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of base-files:
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not configured yet.
dpkg: error processing base-files (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim:
 vim depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing vim (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-core:
 compiz-core depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iproute:
 iproute depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing iproute (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
Setting up pdftk (1.41-2) ...
dpkg: dependency problems prevent configuration of xinit:
 xinit depends on xrdb; however:
  Package xrdb is not installed.
dpkg: error processing xinit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on cpp (>= 4:4.2.3-1ubuntu3); however:
  Version of cpp on system is 4:4.1.2-9ubuntu2.
 g++ depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of perl-tk:
 perl-tk depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing perl-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on libpam-modules; however:
  Package libpam-modules is not configured yet.
dpkg: error processing samba-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaprutil1:
 libaprutil1 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libaprutil1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libcairo2-dev; however:
  Package libcairo2-dev is not configured yet.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserver1.2-9:
 libedataserver1.2-9 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libedataserver1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2-2:
 libsasl2-2 depends on libdb4.6; however:
  Package libdb4.6 is not installed.
dpkg: error processing libsasl2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of passwd:
 passwd depends on libpam-modules (>= 0.72-5); however:
  Package libpam-modules is not configured yet.
dpkg: error processing passwd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-exchange depends on libdb4.6; however:
  Package libdb4.6 is not installed.
 evolution-exchange depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-file:
 apt-file depends on libapt-pkg-perl; however:
  Package libapt-pkg-perl is not configured yet.
dpkg: error processing apt-file (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex:
 openoffice.org-writer2latex depends on openoffice.org-core (>= 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer2latex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on passwd; however:
  Package passwd is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-main:
 compiz-fusion-plugins-main depends on compiz-core; however:
  Package compiz-core is not configured yet.
 compiz-fusion-plugins-main depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing compiz-fusion-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-utils:
 apache2-utils depends on libaprutil1; however:
  Package libaprutil1 is not configured yet.
dpkg: error processing apache2-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-compizconfig:
 python-compizconfig depends on libxcb1; however:
  Package libxcb1 is not installed.
dpkg: error processing python-compizconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-2.6.24-16-generic:
 linux-image-2.6.24-16-generic depends on module-init-tools (>= 3.3-pre11-4ubuntu3); however:
  Version of module-init-tools on system is 3.3-pre4-2ubuntu4.
dpkg: error processing linux-image-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on libpam-modules (>= 0.72-9); however:
  Package libpam-modules is not configured yet.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-mdns:
 libnss-mdns depends on base-files (>= 3.1.10); however:
  Package base-files is not configured yet.
dpkg: error processing libnss-mdns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-plugins depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xutils:
 xutils depends on xcursorgen; however:
  Package xcursorgen is not installed.
 xutils depends on sessreg; however:
  Package sessreg is not installed.
dpkg: error processing xutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on smbclient; however:
  Package smbclient is not configured yet.
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-ttcidfont-conf:
 x-ttcidfont-conf depends on xutils; however:
  Package xutils is not configured yet.
dpkg: error processing x-ttcidfont-conf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libpurple0 (>= 1:2.4.1-1ubuntu2); however:
  Package libpurple0 is not configured yet.
 pidgin depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

```

---

### Post by markofealing on 2008-04-29
I had something similar with my Kubuntu upgrade to 8.04.

Can you login to your system and what do you get when you do?

---

### Post by yang on 2008-04-29
In fact, no I cannot log in to Gnome - after my login is accepted, I am taken to a screen with the brown wallpaper (what is usually seen when Gnome is loading), but then nothing happens, and although I can move the mouse around, nothing I press can cause anything to happen (right-clicking, alt-f2, ctrl-alt-del, etc.).  I can ssh in and I can login on terminals ctrl-alt-1 through 6 - these all work just fine.

---

### Post by yang on 2008-04-29
I'm also just as interested in any hints on how I may begin to debug this situation on my own.

---

### Post by yang on 2008-05-03
*Bump*

Can anyone help? This is somewhat urgent, and so far I have gotten no leads from Forums, IRC, Launchpad, or elsewhere.  Again, I'm willing to put in effort to debug, but I honestly don't know where to start at this point.

Is there such a thing as a repair installation? I just don't look forward to performing a complete reinstall, because I'd have to go through the whole configuration game again to get this workstation integrated into my workplace network.

---

### Post by yang on 2008-05-03
At last!

apt-get install -f got me out of the dependency failure tarpit that was killing my attempts to apt-get install packages and to dpkg --configure -a.  Another thing to try would've been apt-get clean -f.  A subsequent apt-get dist-upgrade worked (took under 3 minutes).

Thanks to JoshuaRL on #ubuntu.

---

### Post by markofealing on 2008-05-06
I'm pleased it worked for you. 

Looks like my system is more terminal (pun intended) as I just get a Terminal window and have to manually run kicker. Even then, I can't move or resize windows or more than one desktop!

Network works, but not much else.

Trying your fix has resulted in a package update, I believe this is a standard update (updates for python and HAL) rather than anything specific to my problem. Therefore, the same problems exist.

I'm close to doing a backup of my home area and a fresh install!

---

### Post by fixitdude on 2008-05-06
Do a

df

At a terminal, I am thinking you ran out of disk space... maybe?

Older installs had the / on it's own partition, and home on another (which to me is the way to go anyway).

Look for "Parted Magic" if you need to stretch partitions.

---

### Post by booksbuggy on 2008-11-02
[http://ubuntuforums.org/showthread.php?t=35087&highlight=system+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=system+backup)

This thread helped keeping me from reinstalling Ubuntu many times, just remember to do the system backup daily and you don't normally have to worry about update failures.

---

### Post by markofealing on 2008-11-06
I'm giving this a try before upgrading to 8.10

[http://www.arsgeek.com/2006/10/18/how-to-back-up-and-restore-your-ubuntu-machine/](http://www.arsgeek.com/2006/10/18/how-to-back-up-and-restore-your-ubuntu-machine/)

Seems quite a neat yet powerful solution.

---

