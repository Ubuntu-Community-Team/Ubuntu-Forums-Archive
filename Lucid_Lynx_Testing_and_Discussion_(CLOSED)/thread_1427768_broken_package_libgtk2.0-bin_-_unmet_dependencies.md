---
title: "broken package: libgtk2.0-bin - unmet dependencies"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xak on 2010-03-11
I just did a fresh install of 10.04 alpha3 and after running a full update with update manager I have a dependency issue with the libgtk2.0-bin package. I am stuck and can't seem to get past without uninstalling ubuntu-desktop and a ton of other packages which really breaks the system (that's what I did the first time and have since reinstalled). Here's the output when trying to upgrade:

```
$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libgtk2.0-bin 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 320kB of archives. After unpacking 16.4kB will be used.
The following packages have unmet dependencies:
  libgtk2.0-bin: Depends: libgtk2.0-0 (>= 2.19.7-0ubuntu1) but 2.19.6-1ubuntu4 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
apturl
brasero
empathy
eog
evince
evolution
evolution-couchdb
evolution-exchange
evolution-indicator
evolution-plugins
gdebi
gnome-applets
gnome-codec-install
gnome-control-center
gnome-icon-theme
gnome-panel
gnome-screensaver
gnome-session
gnome-themes-ubuntu
gucharmap
human-theme
humanity-icon-theme
indicator-applet
indicator-applet-session
indicator-me
indicator-messages
indicator-session
libgtk2.0-bin
light-themes
pitivi
rhythmbox
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-ubuntuone-music-store
simple-scan
software-center
system-config-printer-gnome
totem
totem-mozilla
totem-plugins
ubufox
ubuntu-artwork
ubuntu-desktop
ubuntu-mono

Install the following packages:
lxsession [0.4.1-0ubuntu1 (lucid)]

Leave the following dependencies unresolved:
alacarte recommends gnome-panel
capplets-data recommends gnome-control-center (>= 1:2.29.92-0ubuntu1)
evolution-common recommends evolution
file-roller recommends gnome-icon-theme (>= 2.18)
firefox recommends ubufox
gcalctool recommends gnome-icon-theme
gnome-panel-data recommends gnome-panel
libgtk2.0-0 recommends libgtk2.0-bin
Score is 1121

Accept this solution? [Y/n/q/?] q
```

**EDIT**: Okay, if I just do an 'upgrade' instead of 'dist-upgrade' it doesn't seem to complain too badly and I can install other packages now. So, what *NOT* to do is run 'dist-upgrade' and let it resolve the way it thinks it should.

---

### Post by psyke83 on 2010-03-12
Don't perform a dist-upgrade yet, and read the sticky threads in the development release sub-forum. Your question will be answered.

---

### Post by Kevbert on 2010-03-12
The release of your file should be out any time from now on. See [http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg07986.html](http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg07986.html)

---

### Post by jppr on 2010-03-12
if you have to ask things like this so you should think about whether  you need the wisdom to use development version?

---

### Post by skymera on 2010-03-12
I have the same thing.

I'll let it fix itself. :)

---

### Post by xak on 2010-03-24
Thanks to everyone else who provided useful input.

> **jppr said:**
> if you have to ask things like this so you should think about whether  you need the wisdom to use development version?

jppr: Perhaps you should not be posting to user forums if you cannot properly use the language or provide useful information.

---

