---
title: "apt-get problem"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Luke Kijanovich on 2011-10-17
After trying to run apt-get upgrade/install/update i get following error
```

exec: 19: /usr/share/debconf/frontend: not found
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up bluez (4.96-0ubuntu4) ...
/var/lib/dpkg/info/bluez.postinst: 60: update-rc.d: not found
dpkg: error processing bluez (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of bluez-alsa:
 bluez-alsa depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluez-alsa (--configure):
 dependency problems - leaving unconfigured
Setting up cups (1.5.0-8ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          exec: 19: /usr/share/debconf/frontend: not found
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bluez-cups:No apport report written because MaxReports is reached already

 bluez-cups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up doc-base (0.10.2) ...
/var/lib/dpkg/info/doc-base.postinst: 71: install-docs: not found
dpkg: error processing doc-base (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up cups-bsd (1.5.0-8ubuntu1) ...
exec: 19: /usr/share/debconf/frontend: not found
dpkg: error processing cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 man-db
 bluez
 bluez-alsa
 cups
 bluez-cups
 bluez-gstreamer
 doc-base
 gnome-bluetooth
 cups-bsd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I have absolutely no idea what's wrong :(

---

### Post by zvacet on 2011-10-17
In terminal type

```
sudo dpkg--configure -a
```

---

