---
title: "aborted upgrade from fiesty to gutsy"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by elloello on 2007-12-20
So I tried to upgrade from Fiesty to Gutsy and got a number of dependecy issues during the process, which resulted in an abotred upgrade and now a number of random issues, such as Firefox shutting itself down for no apparent reason midsession, amidst otehr strange things.  I made a list of all of the packages that had issues during the upgrade process.  I'm very new to all of this stuff so any help would be appreciated greatly.

dependency problems - leaving unconfigured
for all of the following packages:
--login
--base-files
--bash
--passwd
--adduser
--fuse-utils
--/var/cache/apt/archives/ntfs-3g_1%  (pre-dependecy problem)
--ssl-cert
--cupsys
--dbus
--libgnomevfs2-0
--libgnome2-0
--libbonboui2-0
--libgnomemeui-0

Then it said:
Could not install the upgrades

The upgrade aborts now.  Your system could be in an unusable state.  A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed

So now my computer thinks it has Gutsy installed, but it is not working correctly.

Does anyone know how I can complete the upgrade?
If not does anyone know a way that I can remove the copy of Ubuntu I currently have on my machine from it's partition and burn a new iso of Gutsy to disk just act like I am doing a first time install of Gutsy?  Like I said I am fairly new to this and I don't really have all that much data I would need to back up or anything.

---

### Post by rsambuca on 2007-12-20
First try opening a terminal and running the command that it indicated:
```
sudo dpkg --configure -a
```

---

### Post by elloello on 2007-12-20
Ok, I tried that and got no results.  There was no output to the command line after running the command and Updtae Manager is still telling me that not all updates can be installed because my previous upgrade did not complete.  Any other ideas?

---

### Post by rsambuca on 2007-12-20
Can you post the outputs of the following:

```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by elloello on 2007-12-20
I'm actually just gonna start with a fresh copy of gutsy from a disk I think.  With firefox constantly closing on me it is a really big pain to even try to post my output.  I have to e-mail it to myself and then send to another computer, which I am typing on now.  I've been having troubles since before I did the upgrade anyway, and I don't have much to lose in starting fresh at this point, plus whatever problems I had should be fixed then.  Thanks for your help though.  Much appreciated.  I will post again if I have any issues after I overwrite the partition.

---

### Post by elloello on 2007-12-20
also this time I am only gonna include the canonical and resrticted software in my software souces list

---

### Post by rsambuca on 2007-12-20
With these types of problems, often a fresh install is easiest.  Your odds of a successful and trouble-free upgrade decrease with each non-standard repository you add.

---

### Post by elloello on 2007-12-20
yeah I figured as much.  I have a duel boot machine with XP on another partion.  Will I be able just overwrite the partition I have my current copy of ubuntu on with my new copy using the live cd, or do I need to first repartition and change the MBR in windows?

---

### Post by PmDematagoda on 2007-12-20
You can just install the new Ubuntu OS over your old one without any problems.

---

### Post by sricketts on 2008-04-23
> **PmDematagoda said:**
> You can just install the new Ubuntu OS over your old one without any problems.

I am having a similar problem with my upgrade from 7.04 to 7.10 (32-bit). Unfortunately, the machine in question has been in use for over a year, and so reinstalling software and restoring data might be a pain. Is there another option?

Thanks,
Scott

Here is the result of dpkg --configure -a

```
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libbonoboui2-0 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd1:
 libgnomekbd1 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgnomekbd1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing gimp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-speech7:
 libgnome-speech7 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgnome-speech7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on metacity-common (>= 1:2.20); however:
  Package metacity-common is not installed.
 metacity depends on metacity-common (<< 1:2.21); however:
  Package metacity-common is not installed.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.0-cil:
 libgnome2.0-cil depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnome2.0-cil depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome2.0-cil depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgnome2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 nautilus-cd-burner depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 nautilus-cd-burner depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
Setting up gedit-common (2.20.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java5-demo:
 sun-java5-demo depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not installed.
dpkg: error processing sun-java5-demo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-pilot-conduits:
 gnome-pilot-conduits depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 gnome-pilot-conduits depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
dpkg: error processing gnome-pilot-conduits (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegroupwise1.2-13:
 libegroupwise1.2-13 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libegroupwise1.2-13 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gnome:
 bluez-gnome depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing bluez-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatspi1.0-0:
 libatspi1.0-0 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libatspi1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeprint2.2-0:
 libgnomeprint2.2-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing libgnomeprint2.2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 gedit depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gedit depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Package libgnomeprint2.2-0 is not configured yet.
 gedit depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
 gedit depends on gedit-common (>= 2.20); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.21); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
 libgnomeui-0 depends on libgnomeui-common (>= 2.20); however:
  Version of libgnomeui-common on system is 2.17.92-0ubuntu1.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sound-juicer:
 sound-juicer depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 sound-juicer depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 sound-juicer depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 sound-juicer depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing sound-juicer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libart2.0-cil:
 libart2.0-cil depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing libart2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomecanvas2-0:
 libgnomecanvas2-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
dpkg: error processing libgnomecanvas2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-gnomevfs:
 gstreamer0.10-gnomevfs depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing gstreamer0.10-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not installed.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-nettool:
 gnome-nettool depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-nettool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libecal1.2-7 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libebook1.2-9 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-9 (>= 1.12.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 1.12.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libegroupwise1.2-13 (>= 1.12.1); however:
  Package libegroupwise1.2-13 is not configured yet.
 evolution-data-server depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 evolution-data-server depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libpanel-applet2-0 depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 rhythmbox depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 rhythmbox depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 rhythmbox depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 rhythmbox depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 rhythmbox depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
 rhythmbox depends on gstreamer0.10-gnomevfs; however:
  Package gstreamer0.10-gnomevfs is not configured yet.
 rhythmbox depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeprintui2.2-0:
 libgnomeprintui2.2-0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnomeprintui2.2-0 depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 libgnomeprintui2.2-0 depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Package libgnomeprint2.2-0 is not configured yet.
dpkg: error processing libgnomeprintui2.2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-gstreamer:
 totem-gstreamer depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 totem-gstreamer depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 totem-gstreamer depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 totem-gstreamer depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 totem-gstreamer depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 totem-gstreamer depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
 totem-gstreamer depends on gstreamer0.10-gnomevfs; however:
  Package gstreamer0.10-gnomevfs is not configured yet.
dpkg: error processing totem-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomecanvas:
 python-gnomecanvas depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 python-gnomecanvas depends on libgnomecanvas2-0 (>= 2.19.1); however:
  Package libgnomecanvas2-0 is not configured yet.
dpkg: error processing python-gnomecanvas (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomebt0:
 libgnomebt0 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnomebt0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomebt0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgnomebt0 depends on libgnomecanvas2-0 (>= 2.19.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 libgnomebt0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnomebt0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2.0-cil:
 libgconf2.0-cil depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgconf2.0-cil depends on libgnome2.0-cil (>= 2.16.0); however:
  Package libgnome2.0-cil is not configured yet.
dpkg: error processing libgconf2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser7:
 libtotem-plparser7 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libtotem-plparser7 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libtotem-plparser7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcompizconfig-backend-gconf:
 libcompizconfig-backend-gconf depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libcompizconfig-backend-gconf depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libcompizconfig-backend-gconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 libgnome-desktop-2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-desktop-2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgnome-desktop-2 depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-desktop-2 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gtkhtml3.14 depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem-xine (>= 2.20.0-0ubuntu3) | totem-gstreamer (>= 2.20.0-0ubuntu3); however:
  Package totem-xine is not installed.
  Package totem-gstreamer is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-7 (>= 1.12.0); however:
  Package libecal1.2-7 is not configured yet.
 evolution-webcal depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 evolution-webcal depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnome-games depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-games depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnomecanvas2-0 (>= 2.19.1); however:
  Package libgnomecanvas2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Package libgnomeprint2.2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeprintui2.2-0 (>= 2.17.0); however:
  Package libgnomeprintui2.2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on liborbit2 (>= 1:2.14.8); however:
  Version of liborbit2 on system is 1:2.14.7-0ubuntu1.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser7 (>= 2.19); however:
  Package libtotem-plparser7 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

```

---

### Post by sricketts on 2008-04-24
Well, I gave up on a quick fix, backed everything up, and did a clean install of 7.10. It was pretty painless.

---

