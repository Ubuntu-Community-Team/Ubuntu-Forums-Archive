---
title: "Urgent!!! dpkg not working or letting me install anying"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by sexisanti on 2010-07-22
I have Ubuntu 8.04 I have tried installing different things like flash plugin I have tried reinstalling dpkg but did not work. it also won't let me upgrade anything because of it  This is what it told me:


Setting up gnome-applets-data (2.22.2-0ubuntu2) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up capplets-data (1:2.22.1-0ubuntu4.1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.22); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.23); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (1:2.22.2-0ubuntu1.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-docs (8.06.1) ...
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-app-install (0.5.2.8-0ubuntu1) ...
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.22.3-0ubuntu2) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.22.2-0ubuntu2) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.22.3.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.22.3.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.22.3.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.22.3.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.22.3-0ubuntu0.1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gdm (2.20.7-0ubuntu1.1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.22.3-0ubuntu2) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (>= 1:2.22); however:
  Package gnome-games-data is not configured yet.
 gnome-games depends on gnome-games-data (<< 1:2.23); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-power-manager (2.22.1-1ubuntu4.1) ...
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-monitor (2.22.3-0ubuntu2) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on deskbar-applet (>= 2.20.0); however:
  Package deskbar-applet is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus-extensions-2.0; however:
  Package nautilus-extensions-2.0 is not installed.
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 139
Setting up tomboy (0.10.2-0ubuntu1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Setting up update-manager (1:0.87.31) ...
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-system-tools (2.22.0-0ubuntu10) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gnome-applets-data
 capplets-data
 gnome-control-center
 gnome-panel-data
 gnome-panel
 gnome-applets
 ubuntu-docs
 alacarte
 gnome-app-install
 apturl
 deskbar-applet
 eog
 evince
 evolution-common
 evolution
 evolution-exchange
 evolution-plugins
 f-spot
 file-roller
 gcalctool
 gdm
 gedit-common
 gedit
 gnome-games-data
 gnome-games
 gnome-power-manager
 gnome-system-monitor
 libdeskbar-tracker
 nautilus
 nautilus-sendto
 nautilus-share
 seahorse
 tomboy
 update-manager
 update-notifier
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


please help me!

---

### Post by sidzen on 2010-07-23
The line "dpkg: dependency problems prevent configuration of update-notifier:" points to a very important aspect of package management that using downloaded deb files does not address.  Please go to [http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html) and begin to solve your problem.
Then check out [http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install ]("http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install")
(it may be of help or it may not).
The Community Help pages at [https://help.ubuntu.com]("https://help.ubuntu.com/") are an immense assistance, too.  
Do not be shy of the command line, for ***apt-get*** is your friend and the most efficient way to avoid the problems you have run into.  Do you know the [PHP]sudo apt-get build-dep[/PHP] command?
Your question is not sufficient for me to know exactly what to tell you, but I hope this helps.

---

### Post by sexisanti on 2010-07-23
yes i know apt-get is my friend its my best friend.... dpkg isn't working and won't let me install, update, remove or upgrade at all.

---

### Post by sidzen on 2010-07-23
Sorry -- cannot help.  Did you try purging it?  {Then (if allows) do a dist-upgrade.}

---

### Post by sexisanti on 2010-07-23
tried to purge did not work.

---

### Post by sidzen on 2010-07-23
I'll defer to others and hope they may help you, sexisanti!

---

