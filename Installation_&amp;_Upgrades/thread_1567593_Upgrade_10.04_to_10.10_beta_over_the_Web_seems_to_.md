---
title: "Upgrade 10.04 to 10.10 beta over the Web seems to partially fail"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by traductionbiz on 2010-09-04
Hi, ;-)

Straight after reading the 10.10 beta announcement, I started the upgrade process after updating my existing install.

Everything seemed to go OK until downloading file 1530 out of 1615. Then the count seemed to stop, although the download time/speed count continued to update. I had to go out briefly so I didn't see the download complete, but when I came back Ubuntu was already into installing the updates. 

That seemed to go OK until I received an error message with exit = 1 (I can't recover the exact message coz I put it in a Tomboy note, and Tomboy currently seems to be broken). The remaining updates did not appear to be applied, and there were lots of messages about not having configured various packages.

But I had no problem restarting the system, and it basically seems to be mostly working, although some things (such as Tomboy Notes) do *not* work.

I re-ran the update manager. The system prompted me to do a partial update involving some 235 packages, which I am now doing... I'll post back with info about how successful it was.

Anyone else had such problems?

---

### Post by traductionbiz on 2010-09-04
During the partial upgrade, I again get the same error message as during the original upgrade: 

"Could not install 'gconf2'

The upgrade will continue but the 'gconf2' package may not be in a working state. Please consider submitting a bug report about it.

subprocess installed post-installation script returned error exit status 1"

When I acknowledge the message, I get this message:

"Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)."

Ubuntu then continues setting-up packages, and finishes with this message:

"Upgrade complete

The upgrade is completed but there were errors during the upgrade process."

After I acknowledge this message, the updater exits silently...

---

### Post by traductionbiz on 2010-09-04
I just tried executing:

sudo dpkg --configure -a

This was the result:

david@linux:~$ sudo dpkg --configure -a
[sudo] password for david: 
Setting up csound-utils (1:5.12.1~dfsg-5) ...
Setting up libmarblewidget10 (4:4.5.1-0ubuntu1) ...
Setting up csound-gui (1:5.12.1~dfsg-5) ...
Setting up libdesktopcouch-glib-1.0-2 (0.6.96-0ubuntu1) ...
Setting up libkpimidentities4 (4:4.5.1-0ubuntu1) ...
Setting up libfolks-telepathy0 (0.1.16-1) ...
Setting up aptdaemon (0.31+bzr476-0ubuntu1) ...
Setting up libkcal4 (4:4.5.1-0ubuntu1) ...
Setting up gconf2 (2.31.7-0ubuntu3) ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 161, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 121, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20-edubuntu'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up alsa-base (1.0.23+dfsg-1ubuntu3) ...
dpkg: dependency problems prevent configuration of gnibbles:
 gnibbles depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnibbles (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-common:
 totem-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing totem-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of celestia-gnome:
 celestia-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing celestia-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up apport (1.14.1-0ubuntu6) ...
start: Job is already running: apport
dpkg: dependency problems prevent configuration of evolution-indicator:
 evolution-indicator depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evolution-indicator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of istanbul:
 istanbul depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 istanbul depends on gstreamer0.10-plugins-good (>= 0.10.3); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing istanbul (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of swell-foop:
 swell-foop depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing swell-foop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnotski:
 gnotski depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnotski (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pitivi:
 pitivi depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing pitivi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screenshot:
 gnome-screenshot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screenshot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firestarter:
 firestarter depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing firestarter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of glines:
 glines depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing glines (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgstfarsight0.10-0:
 libgstfarsight0.10-0 depends on gstreamer0.10-plugins-good (>= 0.10.17-1ubuntu1); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing libgstfarsight0.10-0 (--configure):
 dependency problems - leaving unconfigured
Setting up libkblog4 (4:4.5.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of lightsoff:
 lightsoff depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing lightsoff (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-search-tool:
 gnome-search-tool depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-search-tool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtali:
 gtali depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gtali (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on gstreamer0.10-plugins-good (>= 0.10.0); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gpointing-device-settings:
 gpointing-device-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gpointing-device-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gsynaptics:
 gsynaptics depends on gpointing-device-settings; however:
  Package gpointing-device-settings is not configured yet.
dpkg: error processing gsynaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of camorama:
 camorama depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing camorama (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing seahorse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnect:
 gnect depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnect (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-log:
 gnome-system-log depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-system-log (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
Setting up libktnef4 (4:4.5.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of gnome-media-common:
 gnome-media-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpurple0:
 libpurple0 depends on libgstfarsight0.10-0 (>= 0.0.3); however:
  Package libgstfarsight0.10-0 is not configured yet.
dpkg: error processing libpurple0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-extra:
 compiz-fusion-plugins-extra depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-fusion-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 rhythmbox depends on gstreamer0.10-plugins-good (>= 0.10.7); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-dictionary:
 gnome-dictionary depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-dictionary (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-central ...
Errors were encountered while processing:
 gconf2
 gnibbles
 light-themes
 gnome-applets
 totem-common
 onboard
 gstreamer0.10-plugins-good
 compiz-gnome
 celestia-gnome
 update-manager
 network-manager-gnome
 evolution-indicator
 istanbul
 gnome-session-bin
 swell-foop
 aisleriot
 gnotski
 gnome-power-manager
 pitivi
 gnome-screenshot
 gdm
 firestarter
 glines
 libgstfarsight0.10-0
 lightsoff
 eog
 gnome-search-tool
 gnome-system-monitor
 gconf-editor
 gnome-settings-daemon
 compiz
 gtali
 openoffice.org-gnome
 apturl
 miro
 gpointing-device-settings
 capplets-data
 gsynaptics
 camorama
 seahorse
 gnect
 gnome-system-log
 ubuntuone-client
 gnome-media-common
 gedit
 libpurple0
 software-center
 libgnomevfs2-common
 compiz-fusion-plugins-extra
 rhythmbox
 gnome-dictionary
Processing was halted because there were too many errors."

I posted bug reports via Apport...

Any tips about how to recover would be welcome... I seem to have a number of packages in a broken state...

:popcorn:

---

### Post by traductionbiz on 2010-09-04
I posted a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/630018](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/630018)

:popcorn:

---

