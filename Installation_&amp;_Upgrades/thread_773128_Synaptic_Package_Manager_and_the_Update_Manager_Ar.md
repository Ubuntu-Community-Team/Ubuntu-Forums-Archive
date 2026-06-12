---
title: "Synaptic Package Manager and the Update Manager Aren't Working!!!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ComputerExpertVK on 2008-04-28
Synaptic Package Manager and the Update Manager Aren't Working!!!

This is what it says in an error message...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any ideas?

---

### Post by tamoneya on 2008-04-28
```
sudo dpkg --configure -a
```Should fix the problem

---

### Post by ComputerExpertVK on 2008-04-28
it didn't work...
:(

this is what popped out...
(directly copied from the terminal)

computerexpertvk@computerexpertvk:~$ sudo dpkg --configure -a
Setting up scrollkeeper (0.3.14-15ubuntu1) ...
Rebuilding the database. This may take some time.
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui
                                                                           ^

---

### Post by RATM_Owns on 2008-04-28
Hmm.
I had the same problem when going to Hardy.

I'd reboot and try 
sudo dpkg --configure -a again.

---

### Post by ComputerExpertVK on 2008-04-28
i just got 

dpkg: error processing scrollkeeper (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.22); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.23); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
 nautilus depends on nautilus-data (>= 1:2.22); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.23); however:
  Package nautilus-data is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on doc-base; however:
  Package doc-base is not configured yet.
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus-extensions-2.0; however:
  Package nautilus-extensions-2.0 is not installed.
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on gnome-control-center (>= 1:2.8.0); however:
  Package gnome-control-center is not configured yet.
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scrollkeeper
 capplets-data
 gedit
 doc-base
 nautilus-data
 gnome-control-center
 synaptic
 bug-buddy
 gucharmap
 jockey-gtk
 nautilus
 gnome-applets-data
 ubuntu-desktop
 gnome-utils
 gnome-panel-data
 gthumb
 zenity
 ubuntu-docs
 gnome-applets
 update-manager
 nautilus-sendto
 software-properties-gtk
 gnome-terminal
 gnome-user-guide
 gnome-system-monitor
 apturl
 language-selector
 nautilus-share
 nautilus-cd-burner
 gnome-panel
 gnome-app-install
 fast-user-switch-applet
 alacarte
 update-notifier
 ubufox

---

