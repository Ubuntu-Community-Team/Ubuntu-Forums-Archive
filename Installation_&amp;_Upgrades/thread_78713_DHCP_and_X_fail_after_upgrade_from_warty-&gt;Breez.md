---
title: "DHCP and X fail after upgrade from warty-&gt;Breezy"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2005-10-18
I attempted to follow the instructions at: [http://ubuntuforums.org/showthread.php?t=74990](http://ubuntuforums.org/showthread.php?t=74990)

But found that X didn't work afterwards.  There is a thread on this and a suggestion page at the bottom of : [https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

However, since my network card (natively supported under Warty) doesn't seem to be gaining and IP address through DHCP, the apt-get solution is not yet useable.  I'm not a long time linux user, and don't really know where everything is.  I've looked at /etc/network/interfaces and it seems to be correctly written from examples on how DCHP should be set up.

I'm looking for help getting my network card up and running, and then perhaps some assistance with the X reconfiguration once I'm connected back up to the 'net.  Thank goodness I have 2 systems so I can search for help when one fails.

-Onboard Network card (supported under warty, no problem) fails to work after Breezy update.
-X fails: no error message is printed out, just a grey box with an 'ok' button for the error dump


Thank you for your help.

---

### Post by Nachtengel on 2005-10-18
Well got the network connection working for now, perhaps only a temporary fix:
sudo dhclient eth0

brought connectivity.  Now I can SSH into the box instead of swapping monitor cables back and forth when I need to issue commands.  No garuntees this fix lasts further than a reboot....

Following the links given for fixing X don't seem to help, throws a righteous fit about perl and not setting regions?

---

### Post by Nachtengel on 2005-10-18
doing these commands alternately actually seemed to do something:

user@host:~ $ sudo dpkg --configure --pending
user@host:~ $ sudo apt-get -f install

That is until this past iteration, now I'm kinda stuck for what to do...


user@host:~ $ sudo dpkg --configure --pending
dpkg: dependency problems prevent configuration of x-window-system-core:
 x-window-system-core depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri is not installed.
 x-window-system-core depends on libgl1-mesa; however:
  Package libgl1-mesa is not installed.
 x-window-system-core depends on libglu1-mesa; however:
  Package libglu1-mesa is not installed.
 x-window-system-core depends on xkeyboard-config; however:
  Package xkeyboard-config is not installed.
dpkg: error processing x-window-system-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on mesa-utils; however:
  Package mesa-utils is not installed.
 xbase-clients depends on xset; however:
  Package xset is not installed.
 xbase-clients depends on xmodmap; however:
  Package xmodmap is not installed.
 xbase-clients depends on xdriinfo; however:
  Package xdriinfo is not installed.
 xbase-clients depends on appres; however:
  Package appres is not installed.
 xbase-clients depends on beforelight; however:
  Package beforelight is not installed.
 xbase-clients depends on bitmap; however:
  Package bitmap is not installed.
 xbase-clients depends on editres; however:
  Package editres is not installed.
 xbase-clients depends on fstobdf; however:
  Package fstobdf is not installed.
 xbase-clients depends on iceauth; however:
  Package iceauth is not installed.
 xbase-clients depends on ico; however:
  Package ico is not installed.
 xbase-clients depends on listres; however:
  Package listres is not installed.
 xbase-clients depends on oclock; however:
  Package oclock is not installed.
 xbase-clients depends on smproxy; however:
  Package smproxy is not installed.
 xbase-clients depends on viewres; however:
  Package viewres is not installed.
 xbase-clients depends on x11perf; however:
  Package x11perf is not installed.
 xbase-clients depends on xbiff; however:
  Package xbiff is not installed.
 xbase-clients depends on xcalc; however:
  Package xcalc is not installed.
 xbase-clients depends on xclipboard; however:
  Package xclipboard is not installed.
 xbase-clients depends on xclock; however:
  Package xclock is not installed.
 xbase-clients depends on xconsole; however:
  Package xconsole is not installed.
 xbase-clients depends on xditview; however:
  Package xditview is not installed.
 xbase-clients depends on xev; however:
  Package xev is not installed.
 xbase-clients depends on xeyes; however:
  Package xeyes is not installed.
 xbase-clients depends on xf86dga; however:
  Package xf86dga is not installed.
 xbase-clients depends on xfd; however:
  Package xfd is not installed.
 xbase-clients depends on xfontsel; however:
  Package xfontsel is not installed.
 xbase-clients depends on xgamma; however:
  Package xgamma is not installed.
 xbase-clients depends on xgc; however:
  Package xgc is not installed.
 xbase-clients depends on xkill; however:
  Package xkill is not installed.
 xbase-clients depends on xload; however:
  Package xload is not installed.
 xbase-clients depends on xlogo; however:
  Package xlogo is not installed.
 xbase-clients depends on xlsatoms; however:
  Package xlsatoms is not installed.
 xbase-clients depends on xlsclients; however:
  Package xlsclients is not installed.
 xbase-clients depends on xlsfonts; however:
  Package xlsfonts is not installed.
 xbase-clients depends on xmag; however:
  Package xmag is not installed.
 xbase-clients depends on xman; however:
  Package xman is not installed.
 xbase-clients depends on xmessage; however:
  Package xmessage is not installed.
 xbase-clients depends on xmodmap; however:
  Package xmodmap is not installed.
 xbase-clients depends on xmore; however:
  Package xmore is not installed.
 xbase-clients depends on xrefresh; however:
  Package xrefresh is not installed.
 xbase-clients depends on xset; however:
  Package xset is not installed.
 xbase-clients depends on xsetroot; however:
  Package xsetroot is not installed.
 xbase-clients depends on xsm; however:
  Package xsm is not installed.
 xbase-clients depends on xstdcmap; however:
  Package xstdcmap is not installed.
 xbase-clients depends on xtrap; however:
  Package xtrap is not installed.
 xbase-clients depends on xvidtune; however:
  Package xvidtune is not installed.
 xbase-clients depends on xwd; however:
  Package xwd is not installed.
 xbase-clients depends on xwininfo; however:
  Package xwininfo is not installed.
 xbase-clients depends on xwud; however:
  Package xwud is not installed.
dpkg: error processing xbase-clients (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xlibs:
 xlibs depends on xkeyboard-config; however:
  Package xkeyboard-config is not installed.
dpkg: error processing xlibs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnomemeeting:
 gnomemeeting depends on libopenh323-1.15.3c2 (>= 1.15.6); however:
  Package libopenh323-1.15.3c2 is not installed.
dpkg: error processing gnomemeeting (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 x-window-system-core
 xbase-clients
 xlibs
 gnomemeeting

user@host:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  appres beforelight bitmap editres fstobdf gnome-volume-manager iceauth ico
  libfs6 libgl1-mesa libgl1-mesa-dri libglu1-mesa libnotify0
  libopenh323-1.15.3c2 listres mesa-utils oclock smproxy viewres x11perf xbiff
  xcalc xclipboard xclock xconsole xditview xdriinfo xev xeyes xf86dga xfd
  xfontsel xgamma xgc xkeyboard-config xkill xload xlogo xlsatoms xlsclients
  xlsfonts xmag xman xmessage xmodmap xmore xrefresh xset xsetroot xsm
  xstdcmap xtrap xvidtune xwd xwininfo xwud
Suggested packages:
  libopenh323-dev
Recommended packages:
  totem notification-daemon
The following packages will be REMOVED:
  dbus-glib-1 libhal0 xlibmesa-dri xlibmesa-gl xlibmesa-glu
The following NEW packages will be installed:
  appres beforelight bitmap editres fstobdf iceauth ico libfs6 libgl1-mesa
  libgl1-mesa-dri libglu1-mesa libnotify0 libopenh323-1.15.3c2 listres
  mesa-utils oclock smproxy viewres x11perf xbiff xcalc xclipboard xclock
  xconsole xditview xdriinfo xev xeyes xf86dga xfd xfontsel xgamma xgc
  xkeyboard-config xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman
  xmessage xmodmap xmore xrefresh xset xsetroot xsm xstdcmap xtrap xvidtune
  xwd xwininfo xwud
The following packages will be upgraded:
  gnome-volume-manager
1 upgraded, 55 newly installed, 5 to remove and 468 not upgraded.
4 not fully installed or removed.
Need to get 0B/16.7MB of archives.
After unpacking 37.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libopenh323-1.15.3c2 libglu1-mesa libgl1-mesa libgl1-mesa-dri mesa-utils
  xset xmodmap xdriinfo appres beforelight bitmap editres libfs6 fstobdf
  iceauth ico listres oclock smproxy viewres x11perf xbiff xcalc xclipboard
  xclock xconsole xditview xev xeyes xf86dga xfd xfontsel xgamma xgc xkill
  xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmore xrefresh
  xsetroot xsm xstdcmap xtrap xvidtune xwd xwininfo xwud xkeyboard-config
  libnotify0 gnome-volume-manager
Install these packages without verification [y/N]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 70296 files and directories currently installed.)
Unpacking libopenh323-1.15.3c2 (from .../libopenh323-1.15.3c2_1.15.6-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libopenh323-1.15.3c2_1.15.6-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libopenh323.so.1', which is also in package libopenh323-1.13.2
Errors were encountered while processing:
 /var/cache/apt/archives/libopenh323-1.15.3c2_1.15.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by docboat on 2005-10-19
Well, I had my two days of upgrade hell too: much the same as yourself, in that my xserver was borked. A whole slew of messages about absent links to fonts, monitor not found etc. 

Also, very patchy package upgrade. I used the apt-get upgrade and apt-get dist-upgrade option, and it took forever to download. (Later just got the bittorent download and burned an iso .... much faster)

My solution? (And still working on fixing "broken things":

1. apt-get -f install uesd frequently along wth apt-get update and apt-get --fix-missing. 
2. When I finally got all packages downloaded, I was confronted with the dreaded libofx2 issue - I deleted kmymoney and carried on. 
3. Finally at the failed gdm login, I checked /etc/X11/xorg.conf and found all seemed to be in order .... BTW I checked the pathway given on the wiki for correction, adn my pathway was different - I would verify te path before correcting the xorg.conf section. 
4. dpkg-reconfigure xorg-xserver

I found that my NVIDIA graphics driver did not want the fbdev option - this after much fiddling, as usual ... and then I could reboot into my nice new Breezy. 

But I must say the upgrade was a lot more buggy than I would have liked. A newbie from M$ would not have felt comfortable at all ..... Pity, because Ubuntu is really cool!

---

