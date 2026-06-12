---
title: "Fesity upgrade woes - CD disappeared?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by BlackWoxs on 2007-04-21
I upgrade Edgy to Feisty using the alternate CD. During the install dependency problems started to appear. I left the PC and when I came back it appeared to have finished although a 'sudo aptitude dist-upgrade' still shows lots of errors. When I tried to check the CD it had 'disappeared', a umount and remount made it reappear. 

At the moment I am not game to try a reboot, and hoping the power stays up, since given the number of errors, I doubt my system will come back.

Aptitude shows:
```
~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up libpaper1 (1.1.21build1) ...
mv: cannot move `/etc/papersize.dpkg-inst' to `/ETC/PAPERSIZE.DPKG-INST': No such file or directory
mv: cannot move `/etc/papersize' to `/ETC/PAPERSIZE': No such file or directory
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xpdf-utils:
 xpdf-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing xpdf-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgs-esp8:
 libgs-esp8 depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libgs-esp8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gs-esp:
 gs-esp depends on libgs-esp8; however:
  Package libgs-esp8 is not configured yet.
dpkg: error processing gs-esp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gs-common:
 gs-common depends on gs-esp | gs; however:
  Package gs-esp is not configured yet.
  Package gs is not installed.
  Package gs-esp which provides gs is not configured yet.
dpkg: error processing gs-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ijsgutenprint:
 ijsgutenprint depends on gs-esp (>= 6.53) | gs-gpl (>= 8.01-1) | gs (>= 6.53) | gs-afpl (>= 8.14); however:
  Package gs-esp is not configured yet.
  Package gs-gpl is not installed.
  Package gs is not installed.
  Package gs-afpl is not installed.
dpkg: error processing ijsgutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys:
 cupsys depends on libpaper1; however:
  Package libpaper1 is not configured yet.
 cupsys depends on poppler-utils | xpdf-utils; however:
  Package poppler-utils is not installed.
  Package xpdf-utils which provides poppler-utils is not configured yet.
  Package xpdf-utils is not configured yet.
 cupsys depends on gs-esp; however:
  Package gs-esp is not configured yet.
dpkg: error processing cupsys (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on gs-esp; however:
  Package gs-esp is not configured yet.
 cups-pdf depends on cupsys (>= 1.1.15); however:
  Package cupsys is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2-common (2.18.0.1-0ubuntu1) ...
mv: cannot move `/usr/share/gconf/default.path' to `/USR/SHARE/GCONF/DEFAULT.PATH': No such file or directory
mv: cannot move `/etc/gconf/2/path' to `/ETC/GCONF/2/PATH': No such file or directory

.... lots more ....

until

Errors were encountered while processing:
 powermanagement-interface
 gconf2-common
 clamav-base
 libpaper1
 ubuntu-desktop
 psutils
 gconf2
 gnome-applets
 cupsys
 libgs-esp8
 gstreamer0.10-plugins-good
 gs-esp
 ekiga
 hplip
 gnome-power-manager
 xpdf-utils
 xpdf-reader
 cups-pdf
 enscript
 eog
 gnome-system-monitor
 gconf-editor
 openoffice.org-gnome
 hpijs
 capplets-data
 nautilus-cd-burner
 seahorse
 xpdf
 gnopernicus
 gnome-media-common
 gedit
 sound-juicer
 gnome-app-install
 libgstreamer-gconf0.8-0
 libgconf2-4
 gnomebaker
 bluefish
 gnome-nettool
 gs-esp-x
 libecal1.2-7
 ijsgutenprint
 libgnomevfs2-common
 libebook1.2-9
 evolution-data-server
 libpanel-applet2-0
 rhythmbox
 compiz-plugins
 nautilus-data
 totem-gstreamer
 gnome-cups-manager
 libgnomebt0
Processing was halted because there were too many errors.
```

My guess was that the upgrade modified the CD ROM reference in some manner and was unable to find the files it needed? My apt sources.list includes the first line, added by the update:

```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```

My first thought was to try and reinstall all the local packages, however if I run synaptic the local packages do not have an option to reinstall them.

Any help would be much appreciated.

---

### Post by BlackWoxs on 2007-04-22
> **BlackWoxs said:**
> I upgrade Edgy to Feisty using the alternate CD. During the install dependency problems started to appear. I left the PC and when I came back it appeared to have finished although a 'sudo aptitude dist-upgrade' still shows lots of errors. When I tried to check the CD it had 'disappeared', a umount and remount made it reappear. 

At the moment I am not game to try a reboot, and hoping the power stays up, since given the number of errors, I doubt my system will come back.


OK, so it has been several hours, and I need to use this PC, so I tried a reboot - Feisty came up, at least partial. X is running, icons seem to be missing and a number of applets caused errors at login. If I try to run apt-get now I am still seeing the same errors however first I get a message showing "510 not fully installed or removed":

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
510 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libpaper1 (1.1.21build1) ...
mv: cannot move `/etc/papersize.dpkg-inst' to `/ETC/PAPERSIZE.DPKG-INST': No such file or directory
mv: cannot move `/etc/papersize' to `/ETC/PAPERSIZE': No such file or directory
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 1

```

Any suggestions as to where to next?

---

