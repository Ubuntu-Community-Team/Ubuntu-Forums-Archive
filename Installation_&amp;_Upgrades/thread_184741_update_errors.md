---
title: "update errors"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by zapcojake on 2006-05-30
I have some ongoing update errors I am hoping somebody can help me with, the graphical update manager is not working so when I dist-upgrade I get the following errors:jake@ubuntu64:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
48 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up balsa (2.3.8-1ubuntu3) ...
/var/lib/dpkg/info/balsa.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing balsa (--configure):
 subprocess post-installation script returned error exit status 126
Setting up camorama (0.17-4ubuntu1) ...
/var/lib/dpkg/info/camorama.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing camorama (--configure):
 subprocess post-installation script returned error exit status 126
Setting up capplets-data (2.14.1-0ubuntu11) ...
/var/lib/dpkg/info/capplets-data.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 126
Setting up eog (2.14.1-0ubuntu2) ...
/var/lib/dpkg/info/eog.postinst: line 20: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 126
Setting up evolution (2.6.1-0ubuntu7) ...
/var/lib/dpkg/info/evolution.postinst: line 20: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.6.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gdebi (0.1.4ubuntu13) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27c4
Wrote aliases at 27c4 - 2970
Wrote parents at 2970 - 3330
Wrote literal globs at 3330 - 338c
Wrote suffix globs at 338c - 6784
Wrote full globs at 6784 - 67a8
Wrote magic at 67a8 - c038
Wrote namespace list at c038 - c048
***
/var/lib/dpkg/info/gdebi.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gdebi (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (= 1:2.14.1-0ubuntu11); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-power-manager (2.14.3-0ubuntu11) ...
/var/lib/dpkg/info/gnome-power-manager.postinst: line 18: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (2.14.6-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
                                                                         [ ok ]
/var/lib/dpkg/info/gdm.postinst: line 117: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 126
Setting up update-manager (0.42.2ubuntu22) ...
/var/lib/dpkg/info/update-manager.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-apt (0.4.9-1ubuntu3) ...
/var/lib/dpkg/info/gnome-apt.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-apt (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-btdownload (0.0.22-1ubuntu7) ...
/var/lib/dpkg/info/gnome-btdownload.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-btdownload (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-panel-data (2.14.1-0ubuntu16) ...
/var/lib/dpkg/info/gnome-panel-data.postinst: line 26: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 2.14.1-0ubuntu16); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Setting up yelp (2.14.1-0ubuntu3) ...
/var/lib/dpkg/info/yelp.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing yelp (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on eog (>= 2.12.2); however:
  Package eog is not configured yet.
 gnome-core depends on gnome-control-center (>= 1:2.12.1); however:
  Package gnome-control-center is not configured yet.
 gnome-core depends on gnome-panel (>= 2.12.2); however:
  Package gnome-panel is not configured yet.
 gnome-core depends on gnome-session (>= 2.12.0); however:
  Package gnome-session is not configured yet.
 gnome-core depends on nautilus (>= 2.12.2); however:
  Package nautilus is not configured yet.
 gnome-core depends on yelp (>= 2.12.2); however:
  Package yelp is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-cups-manager (0.31-1.1ubuntu13) ...
/var/lib/dpkg/info/gnome-cups-manager.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-cups-manager (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-keyring-manager (2.14.0-0ubuntu1) ...
/var/lib/dpkg/info/gnome-keyring-manager.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-keyring-manager (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-nettool (2.14.2-0ubuntu1) ...
/var/lib/dpkg/info/gnome-nettool.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-nettool (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-system-monitor (2.14.3-0ubuntu1) ...
/var/lib/dpkg/info/gnome-system-monitor.postinst: line 20: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-system-tools (2.14.0-0ubuntu11) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: line 20: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-utils (2.14.0-0ubuntu5) ...
/var/lib/dpkg/info/gnome-utils.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-utils (--configure):
 subprocess post-installation script returned error exit status 126
Setting up totem-xine (1.4.1-0ubuntu4) ...
/var/lib/dpkg/info/totem-xine.postinst: line 35: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing totem-xine (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-gstreamer (>= 1.4.1-0ubuntu4) | totem-xine (>= 1.4.1-0ubuntu4); however:
  Package totem-gstreamer is not installed.
  Package totem-xine is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.12.2.3); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on evolution (>= 2.4.1); however:
  Package evolution is not configured yet.
 gnome-desktop-environment depends on gdm (>= 2.8.0.6); however:
  Package gdm is not configured yet.
 gnome-desktop-environment depends on gnome-keyring-manager (>= 2.12.0); however:
  Package gnome-keyring-manager is not configured yet.
 gnome-desktop-environment depends on gnome-nettool (>= 1.4.1); however:
  Package gnome-nettool is not configured yet.
 gnome-desktop-environment depends on gnome-system-monitor (>= 2.12.2); however:  Package gnome-system-monitor is not configured yet.
 gnome-desktop-environment depends on gnome-system-tools (>= 1.4.0); however:
  Package gnome-system-tools is not configured yet.
 gnome-desktop-environment depends on gnome-utils (>= 2.12.2-2); however:
  Package gnome-utils is not configured yet.
 gnome-desktop-environment depends on totem (>= 1.2.1); however:
  Package totem is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
Setting up gtetrinet (0.7.9-1) ...
/var/lib/dpkg/info/gtetrinet.postinst: line 25: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gtetrinet (--configure):
 subprocess post-installation script returned error exit status 126
Setting up regexxer (0.8-3ubuntu1) ...
/var/lib/dpkg/info/regexxer.postinst: line 15: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing regexxer (--configure):
 subprocess post-installation script returned error exit status 126
Setting up seahorse (0.8.1-0ubuntu4) ...
/var/lib/dpkg/info/seahorse.postinst: line 26: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gnome-fifth-toe:
 gnome-fifth-toe depends on gnome-desktop-environment (= 1:2.12.2.3); however:
  Package gnome-desktop-environment is not configured yet.
 gnome-fifth-toe depends on balsa; however:
  Package balsa is not configured yet.
 gnome-fifth-toe depends on camorama; however:
  Package camorama is not configured yet.
 gnome-fifth-toe depends on gtetrinet; however:
  Package gtetrinet is not configured yet.
 gnome-fifth-toe depends on pan | evolution (>= 2.0); however:
  Package pan is not installed.
  Package evolution is not configured yet.
 gnome-fifth-toe depends on regexxer; however:
  Package regexxer is not configured yet.
 gnome-fifth-toe depends on seahorse (>= 0.7.5); however:
  Package seahorse is not configured yet.
dpkg: error processing gnome-fifth-toe (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-screensaver (2.14.1-0ubuntu5) ...
/var/lib/dpkg/info/gnome-screensaver.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-screensaver (--configure):
 subprocess post-installation script returned error exit status 126
Setting up gnome-user-share (0.10-0ubuntu1) ...
/var/lib/dpkg/info/gnome-user-share.postinst: line 10: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing gnome-user-share (--configure):
 subprocess post-installation script returned error exit status 126
Setting up openoffice.org-writer (2.0.2-2ubuntu12) ...
Error: '/etc/mailcap' is not in required format -- not updated
       Restore from backup or delete and re-install mime-support package/var/lib/dpkg/info/openoffice.org-writer.postinst: line 24: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing openoffice.org-writer (--configure):
 subprocess post-installation script returned error exit status 126
Setting up openoffice.org-calc (2.0.2-2ubuntu12) ...
Error: '/etc/mailcap' is not in required format -- not updated
       Restore from backup or delete and re-install mime-support package/var/lib/dpkg/info/openoffice.org-calc.postinst: line 24: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing openoffice.org-calc (--configure):
 subprocess post-installation script returned error exit status 126
Setting up openoffice.org-draw (2.0.2-2ubuntu12) ...
Error: '/etc/mailcap' is not in required format -- not updated
       Restore from backup or delete and re-install mime-support package/var/lib/dpkg/info/openoffice.org-draw.postinst: line 24: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing openoffice.org-draw (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-draw (>> 2.0.2); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-math (2.0.2-2ubuntu12) ...
Error: '/etc/mailcap' is not in required format -- not updated
       Restore from backup or delete and re-install mime-support package/var/lib/dpkg/info/openoffice.org-math.postinst: line 24: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing openoffice.org-math (--configure):
 subprocess post-installation script returned error exit status 126
Setting up openoffice.org-common (2.0.2-2ubuntu12) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27c4
Wrote aliases at 27c4 - 2970
Wrote parents at 2970 - 3330
Wrote literal globs at 3330 - 338c
Wrote suffix globs at 338c - 6784
Wrote full globs at 6784 - 67a8
Wrote magic at 67a8 - c038
Wrote namespace list at c038 - c048
***
/var/lib/dpkg/info/openoffice.org-common.postinst: line 82: /usr/bin/update-desktop-database: cannot execute binary file
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common (>> 2.0.2); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-writer (>> 2.0.2); however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc (>> 2.0.2); however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress (>> 2.0.2); however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw (>> 2.0.2); however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math (>> 2.0.2); however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base (>> 2.0.2); however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-xine-firefox-plugin:
 totem-xine-firefox-plugin depends on totem-xine (= 1.4.1-0ubuntu4); however:
  Package totem-xine is not configured yet.
dpkg: error processing totem-xine-firefox-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evolution; however:
  Package evolution is not configured yet.
 ubuntu-desktop depends on evolution-plugins; however:
  Package evolution-plugins is not configured yet.
 ubuntu-desktop depends on gdebi; however:
  Package gdebi is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-btdownload; however:
  Package gnome-btdownload is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-cups-manager; however:
  Package gnome-cups-manager is not configured yet.
 ubuntu-desktop depends on gnome-nettool; however:
  Package gnome-nettool is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 ubuntu-desktop depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
 ubuntu-desktop depends on gnome-screensaver; however:
  Package gnome-screensaver is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-system-tools; however:
  Package gnome-system-tools is not configured yet.
 ubuntu-desktop depends on gnome-utils; however:
  Package gnome-utils is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on openoffice.org; however:
  Package openoffice.org is not configured yet.
 ubuntu-desktop depends on openoffice.org-evolution; however:
  Package openoffice.org-evolution is not configured yet.
 ubuntu-desktop depends on totem; however:
  Package totem is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 balsa
 camorama
 capplets-data
 eog
 evolution
 evolution-plugins
 gdebi
 gnome-control-center
 gnome-power-manager
 gnome-session
 gdm
 update-manager
 gnome-app-install
 gnome-apt
 gnome-btdownload
 gnome-panel-data
 gnome-panel
 nautilus
 yelp
 gnome-core
 gnome-cups-manager
 gnome-keyring-manager
 gnome-nettool
 gnome-system-monitor
 gnome-system-tools
 gnome-utils
 totem-xine
 totem
 gnome-desktop-environment
 gtetrinet
 regexxer
 seahorse
 gnome-fifth-toe
 gnome-screensaver
 gnome-user-share
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 totem-xine-firefox-plugin
 update-notifier
 ubuntu-desktop
Running prelink please wait
E: Sub-process /usr/bin/dpkg returned an error code (1)
jake@ubuntu64:~$

Thanks in advance, Jake

---

### Post by Jussi Kukkonen on 2006-05-30
You could try 
```
sudo apt-get --reinstall install desktop-file-utils
```
that should reinstall */usr/bin/update-desktop-database*.

---

### Post by zapcojake on 2006-05-31
Thanks, it worked lik  champ.  I was also wondering if anybody knows how to get my icons back in my Applications, Places and System tabs, thay are just gone.  They disappeared at the same time my update trouble started.  Thanks

---

