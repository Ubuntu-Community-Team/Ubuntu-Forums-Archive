---
title: "Can't Install Software After Upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by thomasfwilliams on 2011-04-30
Tried to do update via Synaptic after upgrade and received the following info from the terminal:

(Reading database ... 506398 files and directories currently installed.)
Preparing to replace capplets-data 1:2.32.0-0ubuntu2 (using .../capplets-data_1%3a2.32.1-0ubuntu15_all.deb) ...
Unpacking replacement capplets-data ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/capplets-data_1%3a2.32.1-0ubuntu15_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/icons/hicolor/24x24/apps/preferences-desktop-display.png'
No apport report written because MaxReports is reached already
                                                              Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/capplets-data_1%3a2.32.1-0ubuntu15_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.32.1-0ubuntu15); however:
  Version of capplets-data on system is 1:2.32.0-0ubuntu2.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet:
 indicator-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-appmenu:
 indicator-applet-appmenu depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet-appmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-session:
 indicator-applet-session depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 indicator-applet-session depends on indicator-applet (= 0.4.12-0ubuntu1); however:
  Package indicator-applet is not configured yet.
dpkg: error processing indicator-applet-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-complete:
 indicator-applet-complete depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet-complete (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.32); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-dbg:
 gnome-applets-dbg depends on gnome-applets (= 2.32.1.1-0ubuntu5); however:
  Package gnome-applets is not configured yet.
dpkg: error processing gnome-applets-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-dbg:
 gnome-panel-dbg depends on gnome-panel (= 1:2.32.1-0ubuntu6.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-panel-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-dbg:
 gnome-dbg depends on gnome-applets-dbg; however:
  Package gnome-applets-dbg is not configured yet.
 gnome-dbg depends on gnome-panel-dbg; however:
  Package gnome-panel-dbg is not configured yet.
dpkg: error processing gnome-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center
 ubuntu-desktop
 gnome-panel
 indicator-applet
 indicator-applet-appmenu
 indicator-applet-session
 indicator-applet-complete
 gnome-applets
 gnome-applets-dbg
 gnome-panel-dbg
 gnome-dbg
What do I need to do to fix this? Thanks for any help.

---

### Post by mörgæs on 2011-05-01
Which result do you get from booting the machine and running

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by thomasfwilliams on 2011-05-01
Thank you so much for your help, that seems to have solved the problem. I am going to place this in my blog for others. Again, thank you very much!

---

### Post by mörgæs on 2011-05-01
You are welcome. Please mark the thread 'solved'.

You can read more of apt-get in the book in my signature.

---

