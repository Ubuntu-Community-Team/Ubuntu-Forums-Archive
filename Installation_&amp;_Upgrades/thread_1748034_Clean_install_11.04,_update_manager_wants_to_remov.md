---
title: "Clean install 11.04, update manager wants to remove empathy"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Tank Jr on 2011-05-03
Hi all,
I did a clean install of Natty 32 bit on my desktop last Saturday. Now the update manager wants to remove empathy via a partial upgrade. I waited for a day to see if the issue would be resolved, but it isn't. I cannot see the changelog either. On running ```
sudo apt-get update
``` I get the following text. 
```
Ign http://download.skype.com stable InRelease
Ign http://dl.google.com stable InRelease
Ign http://download.skype.com stable Release.gpg
Ign http://linux.dropbox.com maverick InRelease
Ign http://download.skype.com stable Release
Ign http://extras.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://us.archive.ubuntu.com natty-backports InRelease
Get:1 http://dl.google.com stable Release.gpg [197 B]
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Get:2 http://dl.google.com stable Release [1,347 B]
Hit http://linux.dropbox.com maverick Release
Ign http://download.skype.com stable/non-free TranslationIndex
Ign http://us.archive.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty-proposed InRelease
Hit http://archive.canonical.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://download.skype.com stable/non-free i386 Packages
Get:3 http://dl.google.com stable/main i386 Packages [1,157 B]
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Hit http://linux.dropbox.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com natty-backports Release.gpg
Hit http://us.archive.ubuntu.com natty-security Release.gpg
Hit http://archive.canonical.com natty Release
Hit http://extras.ubuntu.com natty Release
Ign http://dl.google.com stable/main TranslationIndex
Ign http://linux.dropbox.com maverick/main TranslationIndex
Ign http://archive.getdeb.net natty-getdeb InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Hit http://us.archive.ubuntu.com natty-proposed Release.gpg
Hit http://us.archive.ubuntu.com natty Release
Hit http://archive.canonical.com natty/partner Sources
Hit http://extras.ubuntu.com natty/main Sources
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Hit http://us.archive.ubuntu.com natty-updates Release
Hit http://us.archive.ubuntu.com natty-backports Release
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://archive.canonical.com natty/partner i386 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Ign http://download.skype.com stable/non-free Translation-en_US
Hit http://us.archive.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com natty-proposed Release
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Ign http://download.skype.com stable/non-free Translation-en
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Hit http://archive.getdeb.net natty-getdeb Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg
Hit http://ppa.launchpad.net natty Release
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com natty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-backports/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-backports/main TranslationIndex
Ign http://linux.dropbox.com maverick/main Translation-en_US
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Ign http://us.archive.ubuntu.com natty-backports/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-security/main Sources
Hit http://us.archive.ubuntu.com natty-security/restricted Sources
Hit http://us.archive.ubuntu.com natty-security/universe Sources
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources
Ign http://linux.dropbox.com maverick/main Translation-en
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-proposed/main i386 Packages
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://us.archive.ubuntu.com natty-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com natty-proposed/universe i386 Packages
Ign http://us.archive.ubuntu.com natty-proposed/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-proposed/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-proposed/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-proposed/universe TranslationIndex
Hit http://archive.getdeb.net natty-getdeb Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty Release
Hit http://ppa.launchpad.net natty/main Sources
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en_US
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main Sources
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://archive.getdeb.net natty-getdeb/apps i386 Packages
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://dl.google.com stable/main Translation-en
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main Sources
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Ign http://archive.getdeb.net natty-getdeb/apps TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-proposed/main Translation-en
Ign http://us.archive.ubuntu.com natty-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-proposed/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-proposed/universe Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en
Fetched 2,701 B in 9s (287 B/s)
Reading package lists...
```
A lot of entries are ignored, is this an issue with the Natty sources being flooded?
Thanks in advance.

---

### Post by cipherboy_loc on 2011-05-03
No, most likely it is because those repositories haven't had any updates. What is the output of:

```

sudo apt-get upgrade -s

```


Cipherboy

---

### Post by Tank Jr on 2011-05-03
Thanks for replying.
The output of ```
sudo apt-get upgrade -s
``` is
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  empathy empathy-common linux-generic linux-headers-generic
  linux-image-generic nautilus-sendto-empathy
The following packages will be upgraded:
  aptdaemon aptdaemon-data gdm gir1.2-panelapplet-3.0 gnome-panel
  gnome-panel-bonobo gnome-panel-data indicator-weather libpanel-applet-3-0
  libpanel-applet2-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  light-themes linux-libc-dev mencoder mplayer mplayer-gui pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-glade2
  python-gtk2 software-center ubuntu-docs ubuntu-sso-client
  unattended-upgrades update-manager update-manager-core usb-creator-common
  usb-creator-gtk vino
39 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Inst ubuntu-docs [11.04.2] (11.04.3 Ubuntu:11.04/natty-proposed [all])
Inst python-glade2 [2.22.0-0ubuntu1] (2.22.0-0ubuntu1.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst python-gtk2 [2.22.0-0ubuntu1] (2.22.0-0ubuntu1.1 Ubuntu:11.04/natty-proposed [i386])
Inst ubuntu-sso-client [1.2.1-0ubuntu1] (1.2.1-0ubuntu2 Ubuntu:11.04/natty-proposed [all])
Inst aptdaemon-data [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Inst python-aptdaemon-gtk [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all]) []
Inst python-aptdaemon.gtk3widgets [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all]) []
Inst aptdaemon [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all]) []
Inst python-aptdaemon.gtkwidgets [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all]) []
Inst python-aptdaemon [0.41+bzr646-0ubuntu2] (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Inst update-manager-core [1:0.150] (1:0.150.2 Ubuntu:11.04/natty-proposed [i386]) [update-manager:i386 ]
Inst update-manager [1:0.150] (1:0.150.2 Ubuntu:11.04/natty-proposed [all])
Inst gdm [2.32.1-0ubuntu3] (2.32.1-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Inst libpanel-applet-3-0 [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Inst gir1.2-panelapplet-3.0 [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Inst gnome-panel-data [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [all])
Inst gnome-panel [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Inst gnome-panel-bonobo [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Inst libpanel-applet2-0 [1:2.32.1-0ubuntu6.4] (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Inst pulseaudio-utils [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst pulseaudio [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst pulseaudio-module-x11 [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst pulseaudio-module-gconf [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst pulseaudio-module-bluetooth [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst pulseaudio-esound-compat [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst libpulse-mainloop-glib0 [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst libpulse-browse0 [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386]) []
Inst libpulse0 [1:0.9.22+stable-queue-24-g67d18-0ubuntu3] (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Inst light-themes [0.1.8.13] (0.1.8.13.1 Ubuntu:11.04/natty-proposed [all])
Inst linux-libc-dev [2.6.38-8.42] (2.6.38-9.43 Ubuntu:11.04/natty-proposed [i386])
Inst mplayer [2:1.0~svn33339~natty] (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Inst mencoder [2:1.0~svn33339~natty] (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Inst mplayer-gui [2:1.0~svn33339~natty] (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Inst software-center [4.0] (4.0.1 Ubuntu:11.04/natty-proposed [all])
Inst unattended-upgrades [0.72.1ubuntu1] (0.72.1ubuntu1.1 Ubuntu:11.04/natty-proposed [all])
Inst usb-creator-gtk [0.2.28] (0.2.28.3 Ubuntu:11.04/natty-updates [all]) []
Inst usb-creator-common [0.2.28] (0.2.28.3 Ubuntu:11.04/natty-updates [all])
Inst vino [2.32.1-0ubuntu2] (2.32.1-0ubuntu2.1 Ubuntu:11.04/natty-updates [i386])
Inst indicator-weather [11.04.24~natty4] (11.05.01~natty1 Weather Indicator PPA:11.04/natty [all])
Conf ubuntu-docs (11.04.3 Ubuntu:11.04/natty-proposed [all])
Conf python-gtk2 (2.22.0-0ubuntu1.1 Ubuntu:11.04/natty-proposed [i386])
Conf python-glade2 (2.22.0-0ubuntu1.1 Ubuntu:11.04/natty-proposed [i386])
Conf ubuntu-sso-client (1.2.1-0ubuntu2 Ubuntu:11.04/natty-proposed [all])
Conf aptdaemon-data (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf python-aptdaemon (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf python-aptdaemon.gtkwidgets (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf python-aptdaemon.gtk3widgets (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf python-aptdaemon-gtk (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf aptdaemon (0.41+bzr657-0ubuntu1 Ubuntu:11.04/natty-proposed [all])
Conf update-manager-core (1:0.150.2 Ubuntu:11.04/natty-proposed [i386])
Conf update-manager (1:0.150.2 Ubuntu:11.04/natty-proposed [all])
Conf gdm (2.32.1-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf libpanel-applet-3-0 (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Conf gir1.2-panelapplet-3.0 (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Conf gnome-panel-data (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [all])
Conf gnome-panel (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Conf gnome-panel-bonobo (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Conf libpanel-applet2-0 (1:2.32.1-0ubuntu6.5 Ubuntu:11.04/natty-proposed [i386])
Conf libpulse0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf libpulse-browse0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio-utils (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio-module-x11 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio-module-gconf (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio-module-bluetooth (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf pulseaudio-esound-compat (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf libpulse-mainloop-glib0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 Ubuntu:11.04/natty-proposed [i386])
Conf light-themes (0.1.8.13.1 Ubuntu:11.04/natty-proposed [all])
Conf linux-libc-dev (2.6.38-9.43 Ubuntu:11.04/natty-proposed [i386])
Conf mplayer (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Conf mencoder (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Conf mplayer-gui (2:1.0~svn33341~natty MPlayer Daily Builds:11.04/natty [i386])
Conf software-center (4.0.1 Ubuntu:11.04/natty-proposed [all])
Conf unattended-upgrades (0.72.1ubuntu1.1 Ubuntu:11.04/natty-proposed [all])
Conf usb-creator-common (0.2.28.3 Ubuntu:11.04/natty-updates [all])
Conf usb-creator-gtk (0.2.28.3 Ubuntu:11.04/natty-updates [all])
Conf vino (2.32.1-0ubuntu2.1 Ubuntu:11.04/natty-updates [i386])
Conf indicator-weather (11.05.01~natty1 Weather Indicator PPA:11.04/natty [all])
```

---

### Post by cipherboy_loc on 2011-05-03
Can you select the empathy updates in Synaptic? What happens if you only select the empathy updates?


Cipherboy

---

### Post by Tank Jr on 2011-05-05
Finally saw what the problem was. Apparently the new empathy had some dependencies that were in the Gnome 3 PPA, which I had not included.
I removed the telepathy PPA and everything works now.

---

