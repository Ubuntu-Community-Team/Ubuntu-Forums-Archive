---
title: "how to upgrade..."
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by xxx6 on 2014-04-17
Hi!

from beta to final?

tia!

---

### Post by QIII on 2014-04-17
Hi!

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get autoremove
```

should do it.

You may want to use synaptic (install it if you don't have it already) to remove older kernels -- but keep the current one and at least the previous one in case of problems.

---

### Post by Bashing-om on 2014-04-17
xxx6; Hi !

Wait untill your mirror site has synced with the release upgrade.
will then have the notification in "Update Manager"
or from terminal
```

sudo do-release-upgrade -d

```

servers are slammed
[INDENT][INDENT]may take longer yet for the mirrors to catch up
[/INDENT][/INDENT]

---

### Post by xxx6 on 2014-04-20
> **Bashing-om said:**
> 
```

sudo do-release-upgrade

```

```
~$ sudo do-release-upgrade
[sudo] password for _: 
Checking for a new Ubuntu release
No new release found

```

:roll:

---

### Post by Iowan on 2014-04-20
> **jesse-8 said:**
> ...

EDIT: **running do-release-upgrade -d allows me to install a development build of 14.04 LTS. I guess I'll go with that now.**You can see if this one works...

---

### Post by xxx6 on 2014-04-20
Nope!

```
~$ sudo do-release-upgrade -d
[sudo] password for _: 
Checking for a new Ubuntu release
No new release found

```

:o

---

### Post by xxx6 on 2014-04-20
> **QIII said:**
> ```
sudo apt-get dist-upgrade
```

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  gnome-control-center-shared-data libcgmanager0 libdmapsharing-3.0-2
  libgpod-common libgpod4 liboxideqt-qmlplugin liboxideqtcore0 libsgutils2-2
  libwayland-egl1-mesa linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
  oxideqt-codecs p11-kit-modules python3-mako python3-markupsafe
  qtdeclarative5-dialogs-plugin qtdeclarative5-privatewidgets-plugin
  rhythmbox-plugins
The following packages will be upgraded:
  gir1.2-rb-3.0 libegl1-mesa libegl1-mesa-drivers libgl1-mesa-glx
  libglapi-mesa libgles2-mesa libpam-systemd librhythmbox-core8
  libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1
  linux-generic linux-headers-generic linux-image-generic p11-kit
  qtdeclarative5-ubuntu-ui-extras-browser-plugin rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  systemd-services udev unity-control-center unity-webapps-qml
  webapp-container webbrowser-app
28 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 89,2 MB of archives.
After this operation, 355 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by deadflowr on 2014-04-20
You were on beta?
Then the do-release-upgrade is meaningless, as you should already be using the trusty sources.

How was the output from post #2?

If you installed beta, then those commands are all you needed to run to get to the final release.

Edit: You posted the output of dist-upgrade and, to me, that seems about right.
Perhaps do it again and select y.

---

### Post by Bashing-om on 2014-04-20
+1

---

### Post by John Jason Jordan on 2014-04-20
I thought I could upgrade my Xubuntu x86_64 13.10 to 14.04 with the desktop DVD instead of over the net. But after booting to the DVD the only options are a complete install. My net connection is not solid enough to chance doing it over the net. And when I originally installed 13.10 it took me nearly a week to get everything configured and all the special programs I need running, so a fresh install is not something I want to go through. Any ideas?

Edit: I discovered that you have to go several screens into the Install option before it finally locates the 13.10 installation. The upgrade option then appears, but is grayed out. The only option that is not grayed out is a fresh install. So I'm still stuck.

---

