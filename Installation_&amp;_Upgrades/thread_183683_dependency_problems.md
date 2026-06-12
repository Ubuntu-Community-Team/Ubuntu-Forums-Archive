---
title: "dependency problems"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by prakkari on 2006-05-28
I have been using ubuntu dapper for some time now and it has always worked smooth but all of the sudden I got this error message while doing upgrade and I cant upgrade or install anything at all really. This is my error message while doing apt-get upgrade:

> root@elias:/home/prakkari# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gconf2-common (2.14.0-1ubuntu2) ...
/var/lib/dpkg/info/ucf.templates: No such file or directory at /usr/share/perl5/Debconf/Template.pm line 107.
dpkg: error processing gconf2-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on gconf2-common (= 2.14.0-1ubuntu2); however:
  Package gconf2-common is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of abiword-gnome:
 abiword-gnome depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing abiword-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dia-gnome:
 dia-gnome depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing dia-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gconf2 depends on gconf2-common (= 2.14.0-1ubuntu2); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomecupsui1.0-1c2a:
 libgnomecupsui1.0-1c2a depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libgnomecupsui1.0-1c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-cups-manager:
 gnome-cups-manager depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnome-cups-manager depends on libgnomecupsui1.0-1c2a (>= 0.31); however:
  Package libgnomecupsui1.0-1c2a is not configured yet.
dpkg: error processing gnome-cups-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-keyring-manager:
 gnome-keyring-manager depends on libgconf2-4 (>= 2.11.1); however:
  Package libgconf2-4 is not configured yet.
 gnome-keyring-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-keyring-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnome-panel depends on libpanel-applet2-0 (>= 2.14.1); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-panel depends on gnome-panel-data (= 2.14.1-0ubuntu16); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgsf-gnome-1-113:
 libgsf-gnome-1-113 depends on libgconf2-4 (>= 2.11.1); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libgsf-gnome-1-113 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgoffice-1-2:
 libgoffice-1-2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgoffice-1-2 depends on libgsf-gnome-1-113 (>= 1.13.99); however:
  Package libgsf-gnome-1-113 is not configured yet.
dpkg: error processing libgoffice-1-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnumeric:
 gnumeric depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnumeric depends on libgoffice-1-2 (>= 0.2.1) | libgoffice-gtk-1-2 (>= 0.2.1); however:
  Package libgoffice-1-2 is not configured yet.
  Package libgoffice-gtk-1-2 is not installed.
 gnumeric depends on libgsf-gnome-1-113 (>= 1.13.99); however:
  Package libgsf-gnome-1-113 is not configured yet.
 gnumeric depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnumeric (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of inkscape:
 inkscape depends on libgconf2-4 (>= 2.11.1); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing inkscape (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-dev:
 libgconf2-dev depends on libgconf2-4 (= 2.14.0-1ubuntu2); however:
  Package libgconf2-4 is not configured yet.
 libgconf2-dev depends on gconf2 (>= 2.14.0-1ubuntu2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgconf2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-dev:
 libpanel-applet2-dev depends on libpanel-applet2-0 (= 2.14.1-0ubuntu16); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing libpanel-applet2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser1:
 libtotem-plparser1 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libtotem-plparser1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 openoffice.org-gtk depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk (= 2.0.2-2ubuntu11); however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of planner:
 planner depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 planner depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing planner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-xine:
 totem-xine depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 totem-xine depends on libtotem-plparser1; however:
  Package libtotem-plparser1 is not configured yet.
 totem-xine depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 totem-xine depends on libtotem-plparser1; however:
  Package libtotem-plparser1 is not configured yet.
dpkg: error processing totem-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-gstreamer (>= 1.4.1-0ubuntu4) | totem-xine (>= 1.4.1-0ubuntu4); however:
  Package totem-gstreamer is not installed.
  Package totem-xine is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-tools:
 gnome-system-tools depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-system-tools depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-system-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of abiword-common:
 abiword-common depends on abiword | abiword-gnome; however:
  Package abiword is not installed.
  Package abiword-gnome is not configured yet.
dpkg: error processing abiword-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2-common
 libgconf2-4
 abiword-gnome
 dia-gnome
 firefox-gnome-support
 gconf2
 gnome-btdownload
 libgnomecupsui1.0-1c2a
 gnome-cups-manager
 gnome-keyring-manager
 libpanel-applet2-0
 gnome-panel-data
 gnome-panel
 gnome-power-manager
 libgsf-gnome-1-113
 libgoffice-1-2
 gnumeric
 inkscape
 libgconf2-dev
 libpanel-applet2-dev
 libtotem-plparser1
 openoffice.org-gtk
 openoffice.org-gnome
 planner
 totem-xine
 totem
 update-manager
 update-notifier
 gnome-system-tools
 abiword-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


can anyone help my with this ?

---

### Post by chiarapat83 on 2006-05-28
Maybe you already know this but... Before doing "apt-get upgrade" you have to do "apt-get update"

---

### Post by prakkari on 2006-05-28
Yeah I know...that works fine, it doesn't just happen when I try to upgrade. It happens when I try to install anything using apt-get. I also tried "dpkg --configure -a" and I tried using dselect but nothing works.

---

### Post by drunknmunky1 on 2008-01-16
I know this is an ancient thread, but this was the first search result on Google, and this problem just popped up for me using Hardy.  Anyway, I think  the reason I had this problem was because /var/lib/dpkg/info got erased for me a while ago, this file: /var/lib/dpkg/info/ucf.templates obviously got erased with it.

I managed to solve the problem by simply creating that file, like so:

sudo vim /var/lib/dpkg/info/ucf.templates
In vim, type :w, then enter    --- this writes the file to the disk even though it's blank
Still in vim, type :q, then enter to quit
then type sudo dpkg -f install and your problem should be fixed! I don't know what this file is for but I didn't have any trouble installing the packages with this file blank.

You can also create this file in gedit, kate, nano or whatever text editor you prefer using.
Hopefully this helps anyone else who ever runs into this issue.

---

