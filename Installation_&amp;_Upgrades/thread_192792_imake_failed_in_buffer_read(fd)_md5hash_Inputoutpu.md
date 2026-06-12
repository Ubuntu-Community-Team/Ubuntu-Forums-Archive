---
title: "imake failed in buffer_read(fd): md5hash: Input/output error"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by markcarey on 2006-06-09
Filed as a bug in malone, as requested by the installer: [https://launchpad.net/distros/ubuntu/+source/imake/+bug/49117](https://launchpad.net/distros/ubuntu/+source/imake/+bug/49117)

During the upgrade from Breezy to Dapper the installer gives the message,

"... failed in buffer_read(fd): md5hash: Input/output error ..."

Luckily enough this doesnt stop Dapper from booting as if you leave things the installer gets far enough to result in a bootable system (Dapper is very snappy ... great work).

Now I am trying to do is use apt-get from the command line (it sort of works as I have mp3 support working) but I keep getting warnings when installing new things. gnome-volume-manager doesnt work - its on the list of things broken.

The full error text from my console is,

root@jersey:/home/mark# apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  gstreamer0.10-plugins-ugly
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
28 not fully installed or removed.
Need to get 181kB of archives.
After unpacking 496kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gstreamer0.10-plugins-ugly 0.10.3-0ubuntu3 [181kB]
Fetched 181kB in 3s (50.8kB/s)
Selecting previously deselected package gstreamer0.10-plugins-ugly.
(Reading database ... 90004 files and directories currently installed.)
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.3-0ubuntu3_i386.deb) ...
Setting up imake (1.0.1-0ubuntu3) ...
dpkg: error processing imake (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems prevent configuration of xutils:
 xutils depends on imake (>= 1:1.0.0) | xmkmf; however:
  Package imake is not configured yet.
  Package xmkmf is not installed.
  Package imake which provides xmkmf is not configured yet.
dpkg: error processing xutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on xutils; however:
  Package xutils is not configured yet.
dpkg: error processing xbase-clients (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksuui1.0-1:
 libgksuui1.0-1 depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing libgksuui1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gnome2-extras:
 python2.4-gnome2-extras depends on libgksuui1.0-1; however:
  Package libgksuui1.0-1 is not configured yet.
dpkg: error processing python2.4-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python2.4-gnome2-extras; however:
  Package python2.4-gnome2-extras is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on python-gnome2-extras (>= 2.10); however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu1.2-1:
 libgksu1.2-1 depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing libgksu1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu1.2-1 (>= 1.3.3); however:
  Package libgksu1.2-1 is not configured yet.
 gksu depends on libgksuui1.0-1; however:
  Package libgksuui1.0-1 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 1.3.6-1); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gksu (>= 1.0.7); however:
  Package gksu is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-gnome2-extras (>= 2.11.3); however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-netstatus-applet:
 gnome-netstatus-applet depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing gnome-netstatus-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on libgksu1.2-1 (>= 1.3.3); however:
  Package libgksu1.2-1 is not configured yet.
 gnome-system-monitor depends on libgksuui1.0-1; however:
  Package libgksuui1.0-1 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on libgksuui1.0-1; however:
  Package libgksuui1.0-1 is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gsfonts-x11:
 gsfonts-x11 depends on xutils (>= 4.1.0-12); however:
  Package xutils is not configured yet.
dpkg: error processing gsfonts-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client:
 hwdb-client depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
dpkg: error processing hwdb-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hwdb-client; however:
  Package hwdb-client is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on xutils (>= 4.0.2); however:
  Package xutils is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of serpentine:
 serpentine depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing serpentine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ttf-arphic-bkai00mp:
 ttf-arphic-bkai00mp depends on xutils (>= 4.0.2); however:
  Package xutils is not configured yet.
dpkg: error processing ttf-arphic-bkai00mp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ttf-arphic-ukai:
 ttf-arphic-ukai depends on xutils (>= 4.0.2); however:
  Package xutils is not configured yet.
dpkg: error processing ttf-arphic-ukai (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ttf-arphic-uming:
 ttf-arphic-uming depends on xutils (>= 4.0.2); however:
  Package xutils is not configured yet.
dpkg: error processing ttf-arphic-uming (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-ttcidfont-conf:
 x-ttcidfont-conf depends on xutils; however:
  Package xutils is not configured yet.
dpkg: error processing x-ttcidfont-conf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ttf-thai-tlwg:
 ttf-thai-tlwg depends on x-ttcidfont-conf; however:
  Package x-ttcidfont-conf is not configured yet.
dpkg: error processing ttf-thai-tlwg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-window-system-core:
 x-window-system-core depends on xbase-clients; however:
  Package xbase-clients is not configured yet.
 x-window-system-core depends on xutils; however:
  Package xutils is not configured yet.
dpkg: error processing x-window-system-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on deskbar-applet; however:
  Package deskbar-applet is not configured yet.
 ubuntu-desktop depends on gdebi; however:
  Package gdebi is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-netstatus-applet; however:
  Package gnome-netstatus-applet is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal-device-manager; however:
  Package hal-device-manager is not configured yet.
 ubuntu-desktop depends on hwdb-client; however:
  Package hwdb-client is not configured yet.
 ubuntu-desktop depends on serpentine; however:
  Package serpentine is not configured yet.
 ubuntu-desktop depends on ttf-arphic-ukai; however:
  Package ttf-arphic-ukai is not configured yet.
 ubuntu-desktop depends on ttf-arphic-uming; however:
  Package ttf-arphic-uming is not configured yet.
 ubuntu-desktop depends on ttf-thai-tlwg; however:
  Package ttf-thai-tlwg is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on x-ttcidfont-conf; however:
  Package x-ttcidfont-conf is not configured yet.
 ubuntu-desktop depends on x-window-system-core; however:
  Package x-window-system-core is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up gstreamer0.10-plugins-ugly (0.10.3-0ubuntu3) ...
Errors were encountered while processing:
 imake
 xutils
 xbase-clients
 libgksuui1.0-1
 python2.4-gnome2-extras
 python-gnome2-extras
 deskbar-applet
 libgksu1.2-1
 gksu
 gdebi
 gdm
 gnome-app-install
 gnome-netstatus-applet
 gnome-system-monitor
 gnome-volume-manager
 gsfonts-x11
 hwdb-client
 hal-device-manager
 msttcorefonts
 serpentine
 ttf-arphic-bkai00mp
 ttf-arphic-ukai
 ttf-arphic-uming
 x-ttcidfont-conf
 ttf-thai-tlwg
 update-notifier
 x-window-system-core
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jersey:/home/mark#

Now the offending deb appears to be,

root@jersey:/home/mark# locate imake*.deb
/var/cache/apt/archives/imake_1%3a1.0.1-0ubuntu3_i386.deb
root@jersey:/home/mark# md5sum /var/cache/apt/archives/imake_1%3a1.0.1-0ubuntu3_i386.deb
0307a9e443fb3fc253c4714c64e8fbfc /var/cache/apt/archives/imake_1%3a1.0.1-0ubuntu3_i386.deb

What should the imake md5sum be?

How do i patch up the system?

The upgrade wizard didnt get far enough to do the cleaning upstage.  
Can I run the uprgade to Dapper wizard from Dapper? 
get a new imake deb install that and then weed through the list by hand?

Thanks

Mark Carey

---

### Post by markcarey on 2006-06-09
Fixed by doing,

dpkg -i imake_1%3a1.0.1-0ubuntu3_i386.deb

dpkg --configure -a

Not a bug. Just installer weirdness

---

