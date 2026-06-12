---
title: "apt-get crash in middle of upgrade"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by ryanc on 2007-04-04
Last night I was running an apt-get upgrade and mid way through I closed the lid to my laptop. For some reason this caused my computer to freeze solid. Upon restarting I have tried to continue the upgrade only to find the output below. Can anyone help me through this?


```
$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up libkonq4 (3.5.6-0ubuntu19) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libkonq4 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdesktop:
 kdesktop depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
dpkg: error processing kdesktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-kio-plugins:
 kdebase-kio-plugins depends on kdesktop; however:
  Package kdesktop is not configured yet.
dpkg: error processing kdebase-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on kdebase-kio-plugins; however:
  Package kdebase-kio-plugins is not configured yet.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok-xine:
 amarok-xine depends on amarok (= 2:1.4.5-0ubuntu7); however:
  Package amarok is not configured yet.
 amarok-xine depends on amarok; however:
  Package amarok is not configured yet.
dpkg: error processing amarok-xine (--configure):
 dependency problems - leaving unconfigured
Setting up libnspr4 (1.firefox2.0.0.3+1-0ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libnspr4 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libnss3:
 libnss3 depends on libnspr4; however:
  Package libnspr4 is not configured yet.
dpkg: error processing libnss3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libnspr4 (>= 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1); however:
  Package libnspr4 is not configured yet.
 firefox depends on libnss3 (>= 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1); however:
  Package libnss3 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 2.0.0.3+1-0ubuntu2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kicker:
 kicker depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kicker (>= 4:3.5.5-1); however:
  Package kicker is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepasswd:
 kdepasswd depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
dpkg: error processing kdepasswd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfind:
 kfind depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
dpkg: error processing kfind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
 konqueror depends on kcontrol (= 4:3.5.6-0ubuntu19); however:
  Package kcontrol is not configured yet.
 konqueror depends on kdebase-kio-plugins (= 4:3.5.6-0ubuntu19); however:
  Package kdebase-kio-plugins is not configured yet.
 konqueror depends on kdesktop (= 4:3.5.6-0ubuntu19); however:
  Package kdesktop is not configured yet.
 konqueror depends on kfind (= 4:3.5.6-0ubuntu19); however:
  Package kfind is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase:
 kdebase depends on kcontrol (>= 4:3.5.6-0ubuntu19); however:
  Package kcontrol is not configured yet.
 kdebase depends on kdebase-kio-plugins (>= 4:3.5.6-0ubuntu19); however:
  Package kdebase-kio-plugins is not configured yet.
 kdebase depends on kdepasswd (>= 4:3.5.6-0ubuntu19); however:
  Package kdepasswd is not configured yet.
 kdebase depends on kdesktop (>= 4:3.5.6-0ubuntu19); however:
  Package kdesktop is not configured yet.
 kdebase depends on kfind (>= 4:3.5.6-0ubuntu19); however:
  Package kfind is not configured yet.
 kdebase depends on kicker (>= 4:3.5.6-0ubuntu19); however:
  Package kicker is not configured yet.
 kdebase depends on konqueror (>= 4:3.5.6-0ubuntu19); however:
  Package konqueror is not configured yet.
 kdebase depends on libkonq4 (>= 4:3.5.6-0ubuntu19); however:
  Package libkonq4 is not configured yet.
dpkg: error processing kdebase (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knewsticker:
 knewsticker depends on kicker; however:
  Package kicker is not configured yet.
dpkg: error processing knewsticker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork:
 kdenetwork depends on knewsticker (>= 4:3.5.6-0ubuntu9); however:
  Package knewsticker is not configured yet.
dpkg: error processing kdenetwork (--configure):
 dependency problems - leaving unconfigured
Setting up qt3-dev-tools (3.3.8really3.3.7-0ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing qt3-dev-tools (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt3-mt-dev:
 libqt3-mt-dev depends on qt3-dev-tools (= 3:3.3.8really3.3.7-0ubuntu4); however:
  Package qt3-dev-tools is not configured yet.
dpkg: error processing libqt3-mt-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on firefox | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-browser | galeon | konqueror; however:
  Package firefox is not configured yet.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape-browser is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package konqueror is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libkonq4
 kdesktop
 kdebase-kio-plugins
 amarok
 amarok-xine
 libnspr4
 libnss3
 firefox
 firefox-gnome-support
 kicker
 kcontrol
 kdepasswd
 kfind
 konqueror
 kdebase
 knewsticker
 kdenetwork
 qt3-dev-tools
```

---

### Post by ryanc on 2007-04-04
It appears the root cause is some corrupted executable judging by this output:

[I]Setting up libkonq4 (3.5.6-0ubuntu19) ...
dpkg (subprocess): unable to execute post-installation script: **Exec format error**[/I]

How can I find out which executable is causing that error?

---

### Post by ryanc on 2007-04-04
I managed to fix my issue using the following commands for each package it was complaining about not being configured correctly.

```

cd /var/cache/apt/archives
dpkg --force-all -i packagename.deb

```

---

