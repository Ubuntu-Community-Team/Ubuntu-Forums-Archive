---
title: "apt-get install always fails with dpkg error"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by bingasedu on 2014-06-06
I'm having trouble getting any apt-get install command to work. They all fail with some dpkg warnings and an error concerning root's PATH. I have no idea why root's PATH might have changed, and I don't know the correct way to fix root's PATH, or root's PATH as seen by sudo. Here an example:
```

$ sudo apt-get install gnome-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil49 libdb5.1-java appmenu-gtk ttf-sil-gentium
  libkadm5clnt-mit7 libglpng g++-4.4 linux-headers-3.2.0-56 libdb5.1-java-gcj
  libpostproc51 libstdc++6-4.4-dev libdirectfb-extra libsysfs-dev
  libpod-coverage-perl libavformat52 libdirectfb-dev appmenu-qt
  libdb4.7-java-gcj libx264-85 libdevel-symdump-perl
  linux-headers-3.2.0-56-generic-pae libxcb-render-util0-dev libjpeg62-dev
  liblzo2-2 python2.6-dev libkadm5srv-mit7 libdb4.7-java libavcodec52
  libid3tag0 libkdb5-4 libreadline5 libmpcdec3 libtest-pod-perl appmenu-gtk3
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dconf-tools epiphany-browser epiphany-browser-data fonts-cantarell
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-applets gnome-backgrounds
  gnome-contacts gnome-icon-theme-extras gnome-js-common gnome-panel
  gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard
  libcaribou-common libcaribou0 libgjs0c libmutter0 libseed-gtk3-0
  mutter-common notification-daemon
Suggested packages:
  epiphany-extensions gnome-netstatus-applet deskbar-applet cpufrequtils gnome
  desktop-base
The following packages will be REMOVED:
  libgail-gnome-module libgnomepanel2.24-cil libpanel-applet2-0 tsclient
The following NEW packages will be installed:
  dconf-tools epiphany-browser epiphany-browser-data fonts-cantarell
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-applets gnome-backgrounds
  gnome-contacts gnome-core gnome-icon-theme-extras gnome-js-common
  gnome-panel gnome-session-fallback gnome-shell gnome-shell-common
  gnome-themes-standard libcaribou-common libcaribou0 libgjs0c libmutter0
  libseed-gtk3-0 mutter-common notification-daemon
0 upgraded, 41 newly installed, 4 to remove and 9 not upgraded.
Need to get 0 B/20.7 MB of archives.
After this operation, 46.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable.
dpkg: error: 2 expected programs not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
$ 
```
Thank you for any help with this.

---

### Post by steeldriver on 2014-06-06
Hmm... what does

```

sudo grep ^Defaults /etc/sudoers

```

say?

---

### Post by bingasedu on 2014-06-06
This:```
$ sudo grep ^Defaults /etc/sudoers
Defaults    env_reset
$
```

---

### Post by steeldriver on 2014-06-06
What version of Ubuntu do you have? afaik the standard version of the sudoers file on Ubuntu should have a secure_path definition

```
Defaults        env_reset[B]
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"[/B]
```

however I'm leery about suggesting you should modify yours without understanding why it's been configured that way. If you do decide to modify it, be sure to use visudo i.e.

```

sudo visudo

```

---

### Post by bingasedu on 2014-06-06
Appologies for not including that orignially. I'm using 12.04 LTS, and it's acting strange in many ways. I'm hoping that getting apt-get install to work will allow me to get things "back to normal". Oh my - I just tried sudo visudo and got this result:
```
$ sudo visudo
[sudo] password for leighton: 
sudo: visudo: command not found
$

```
This system is not acting normally at all...

---

### Post by bingasedu on 2014-06-06
I was able to login as root, locate visudo, and add this line to /etc/sudoers:
```

Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

```
That appears to have resolved the apt-get install problems. I wish I knew how this problem arose, but at least it's solved. Thanks very much for your help!

---

