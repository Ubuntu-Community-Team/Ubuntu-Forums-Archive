---
title: "Upgrading from 10.04 LTS to 12.04 LTS has broken apt-get"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by relli10 on 2012-12-22
Hi,

I have just tried updating my 10.04 LTS desktop system to 12.04 LTS desktop, within Gnome, which seemed to be successful. On rebooting I was presented at the user login screen where my password was not being accepted. It would accept, the screen would flash black and then it would return back to the login screen. I did a bit of searching and executed the following:

```
rm ~/.Xauthority
```

This solved the login screen problem, but now I have discovered that apt-get is not working as I had some SSH error appear in the desktop environment. When I try an  install a package with apt-get I get an error as follows:

```
... You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: openssh-client (< 1:5.9p1-4) but 1:5.3p1-3ubuntu7 is to be installed
               Breaks: openssh-server (< 1:5.9p1-4) but 1:5.3p1-3ubuntu7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

When I run sudo apt-get -f install command, I get the following output:

```
ubuntu@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 python-opengl gir1.2-json-1.0 gir1.2-gconf-2.0 libavutil49
  libqt4-assistant xulrunner-1.9.2 appmenu-gtk libindicator0
  linux-headers-2.6.32-43 libkadm5clnt-mit7 libupsclient1 gcc-4.3-base
  libdbusmenu-glib1 libaprutil1-dbd-sqlite3 msr-tools g++-4.4 libqt4-test
  gir1.2-clutter-1.0 libgraphite3 libglew1.5 libevview2 libindicate-gtk2
  python-gtkglext1 libmono-system-runtime2.0-cil libdns64 libapr1
  libpostproc51 libaccess-bridge-java-jni libqt4-core libstdc++6-4.4-dev
  libaprutil1-ldap libaccess-bridge-java openoffice.org-l10n-common
  libdirectfb-extra libsysfs-dev seed librasqal2 libboost-thread1.38.0
  libseed-gtk3-0 libavformat52 libisccc60 cpu-checker python-gtkspell
  libdirectfb-dev appmenu-qt libido-0.1-0 libx264-85 libgmime2.4-cil
  libmcrypt4 libdirectfb-1.2-9 libjs-mootools liblwres60 libqt4-gui
  libprotobuf5 libesd0 libqtassistantclient4 libdbus-1-dev libdbusmenu-gtk1
  libxcb-render-util0-dev libjpeg62-dev mbr libgirepository1.0-0 libbind9-60
  libimobiledevice0 libevdocument2 libavfilter0 libnunit2.4-cil
  gnome-js-common libaudiofile1 libdbus-glib-1-dev ttf-kacst-one libgdata6
  libappindicator0 php5-mcrypt libqt4-designer libkadm5srv-mit7 libisccfg60
  cups-pk-helper libavcodec52 openoffice.org-l10n-en-gb gir1.2-cogl-1.0
  libindicate4 libid3tag0 cpp-4.3 python-wnck libkdb5-4 dbconfig-common
  libboost-filesystem1.38.0 libisc60 linux-headers-2.6.32-43-generic
  libaprutil1 libreadline5 gir1.2-coglpango-1.0 libprotoc5 appmenu-gtk3
  freeglut3 libboost-system1.38.0 openvpn-blacklist gir1.2-panelapplet-4.0
  libboost-python1.38.0 libavdevice52 python-indicate
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openssh-client openssh-server
Suggested packages:
  libpam-ssh keychain monkeysphere openssh-blacklist openssh-blacklist-extra
  rssh molly-guard
The following packages will be upgraded:
  openssh-client openssh-server
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
Need to get 0 B/1,302 kB of archives.
After this operation, 489 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of openssh-client:
 libssl1.0.0 (1.0.1-4ubuntu5.5) breaks openssh-client (<< 1:5.9p1-4) and is installed.
  Version of openssh-client to be configured is 1:5.3p1-3ubuntu7.
dpkg: error processing openssh-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-client (= 1:5.3p1-3ubuntu7); however:
  Package openssh-client is not configured yet.
 libssl1.0.0 (1.0.1-4ubuntu5.5) breaks openssh-server (<< 1:5.9p1-4) and is installed.
  Version of openssh-server to be configured is 1:5.3p1-3ubuntu7.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-client; however:
  Package openssh-client is not configured yet.
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-askpass-gnome:
 ssh-askpass-gnome depends on openssh-client | ssh (>= 1:1.2pre7-4) | ssh-krb5; however:
  Package openssh-client is not configured yet.
  Package ssh is not configured yet.
  PaNo apport report written because the error message indicates its a followup error from a previous failure.
                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              ckage ssh-krb5 is not installed.
dpkg: error processing ssh-askpass-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ssh-askpass-gnome; however:
  Package ssh-askpass-gnome is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-client
 openssh-server
 ssh
 ssh-askpass-gnome
 ubuntu-desktop
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is anybody able to help me solve this issue? I really don't want to have to install the distro from scratch.

Also, im not sure if it will affect anything but prior to upgrading to 12.04, I migrated this system form Intel hardware to AMD hardware while running 10.04. It was running stable on 10.04.  

Thanks
Paul

---

### Post by 2F4U on 2012-12-23
Found a identically looking problem here:

[http://ubuntuforums.org/showthread.php?t=2084065](http://ubuntuforums.org/showthread.php?t=2084065)

---

### Post by lykwydchykyn on 2012-12-23
Try removing ssh and openssh-server, then you can reinstall them after the update is complete.  When you get in these kinds of situations, it's usually best to figure out which package (or packages) is being a problem and remove it temporarily so the upgrade can finish up.

You might want to double-check your repositories to remove any third-party or ppa repos, if you have them.  These can really mess up a version upgrade.

---

