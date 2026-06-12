---
title: "Python-central not configured, pkginstall terminator not installed!"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by xardas on 2008-05-03
After trying to upgrade to hardy using both the alternate CD and the internet something weird has happened. The upgrade seems to have happened for the most part. Although some things are not working like compiz and some settings. Anyway the synaptic package manager and the apt-get doesn't work no more. It tells me to run  'dpkg --configure -a' and then shuts down. When I run this command in the terminal a long list of errors is shown which look like this one:

Python-central not configured, pkginstall terminator not installed
post-installation script returned error exit status 1

It goes on to give a long list of packages that have not been configured because python-central is not configured.

Does anyone have any idea how I can get synaptic working again. I can't install any new packages man?

---

### Post by xardas on 2008-05-05
Here is the full message that is displayed when I run the command "sudo dpkg --configure -a": 

[COLOR="Red"]Setting up python-central (0.6.5ubuntu1) ...
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
dpkg: error processing python-central (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of displayconfig-gtk:
 displayconfig-gtk depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing displayconfig-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-numeric:
 python-numeric depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
dpkg: error processing python-numeric (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of launchpad-integration:
 launchpad-integration depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing launchpad-integration (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gst0.10:
 python-gst0.10 depends on python-central (>= 0.6); however:
  Package python-central is not configured yet.
dpkg: error processing python-gst0.10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-launchpad-bugs:
 python-launchpad-bugs depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-launchpad-bugs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-virtkey:
 python-virtkey depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
dpkg: error processing python-virtkey (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
 onboard depends on python-virtkey (>= 0.50); however:
  Package python-virtkey is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-bittorrent:
 python-bittorrent depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-bittorrent (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on python-apt; however:
  Package python-apt is not configured yet.
 apturl depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.3.4); however:
  Package language-selector-common is not configured yet.
 language-selector depends on python-apt (>= 0.6.12); however:
  Package python-apt is not configured yet.
 language-selector depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on python-apt (>= 0.6.20ubuntu16); however:
  Package python-apt is not configured yet.
 python-software-properties depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-launchpad-integration:
 python-launchpad-integration depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-launchpad-integration (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-apt (>= 0.7.4ubuntu4); however:
  Package python-apt is not configured yet.
 gnome-app-install depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
 gnome-app-install depends on python-launchpad-integration; however:
  Package python-launchpad-integration is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-apt; however:
  Package python-apt is not configured yet.
 python-apport depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
 python-apport depends on python-launchpad-bugs (>= 0.2.11); however:
  Package python-launchpad-bugs is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi-core:
 gdebi-core depends on python-apt (>= 0.7.0); however:
  Package python-apt is not configured yet.
 gdebi-core depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing gdebi-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bittorrent:
 bittorrent depends on python-bittorrent (= 3.4.2-11ubuntu5); however:
  Package python-bittorrent is not configured yet.
dpkg: error processing bittorrent (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gmenu:
 python-gmenu depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-gmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python-gmenu (= 2.22.1-0ubuntu1); however:
  Package python-gmenu is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-cairo:
 python-cairo depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
dpkg: error processing python-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-menus (>= 2.15.4.1); however:
  Package gnome-menus is not configured yet.
 alacarte depends on python-central (>= 0.5.62); however:
  Package python-central is not configured yet.
 alacarte depends on python-gmenu (>= 2.15.4.1); however:
  Package python-gmenu is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-menus (>= 2.12.0); however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest:
 hwtest depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing hwtest (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-gtk:
 hwtest-gtk depends on hwtest; however:
  Package hwtest is not configured yet.
dpkg: error processing hwtest-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-problem-report:
 python-problem-report depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing python-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python-apt; however:
  Package python-apt is not configured yet.
 command-not-found depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
dpkg: error processing command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on jockey-common (= 0.3.3-0ubuntu7); however:
  Package jockey-common is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-cairo (>= 1.0.2-1.1); however:
  Package python-cairo is not configured yet.
 python-gtk2 depends on python-numeric (>= 24.2-3); however:
  Package python-numeric is not configured yet.
 python-gtk2 depends on python2.4-cairo; however:
  Package python2.4-cairo is not installed.
  Package python-cairo which provides python2.4-cairo is not configured yet.
 python-gtk2 depends on python2.4-numeric; however:
  Package python2.4-numeric is not installed.
  Package python-numeric which provides python2.4-numeric is not configured yet.
 python-gtk2 depends on python2.5-cairo; however:
  Package python2.5-cairo is not installed.
  Package python-cairo which provides python2.5-cairo is not configured yet.
 python-gtk2 depends on python2.5-numeric; however:
  Package python2.5-numeric is not installed.
  Package python-numeric which provides python2.5-numeric is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alacarte; however:
  Package alacarte is not configured yet.
 ubuntu-desktop depends on gdebi; however:
  Package gdebi is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-menus; however:
  Package gnome-menus is not configured yet.
 ubuntu-desktop depends on hwtest-gtk; however:
  Package hwtest-gtk is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-selector is not configured yet.
 ubuntu-desktop depends on launchpad-integration; however:
  Package launchpad-integration is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-notify:
 python-notify depends on python-gtk2 (>= 2.10); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus-extensions-2.0; however:
  Package nautilus-extensions-2.0 is not installed.
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.43); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on gnome-control-center (>= 1:2.8.0); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-terminal (--configure):
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
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on gnome-menus (>= 2.11.1-1); however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python-gtk2 (>= 2.9.7); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtkhtml2:
 python-gtkhtml2 depends on python-gtk2 (>= 2.9.2); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gtkhtml2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on python-gtk2 (>= 2.10.0); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 python-gnome2-desktop depends on python2.4-gtk2; however:
  Package python2.4-gtk2 is not installed.
  Package python-gtk2 which provides python2.4-gtk2 is not configured yet.
 python-gnome2-desktop depends on python2.5-gtk2; however:
  Package python2.5-gtk2 is not installed.
  Package python-gtk2 which provides python2.5-gtk2 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-vte:
 python-vte depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-vte (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)
[/COLOR]

Can anyone tell me how to get my package manager working again???

---

### Post by xardas on 2008-05-07
So no one has any idea abt this. Do I have to reinstall Ubuntu now and delete everything?

---

### Post by menachem on 2008-05-08
I had the same issue while doing an upgrade. I couldn't do anything else because every time I tried to install a package, it exited with the same error.

The installer recommends trying 

```
sudo dpkg --configure -a
```

but that didn't work for me. Some searching online showed people recommending 

```
sudo dpkg --configure -a --force all
```

I did that, ignored the warnings and it worked. It finished configuring a bunch of packages (over 500), warning every time that python-central wasn't configured properly.

Once it was done I was able to figure out that python-central was depending on **clive**, which wasn't installed (I'd uninstalled it in Feisty because it was useless). I ran

```
sudo apt-get install clive
```

which solved that problem. I was then able to run

```
sudo apt-get update && sudo apt-get upgrade
```

and make sure all the packages were properly installed.

---

### Post by xardas on 2008-05-14
Thanks. Let me try it.

---

