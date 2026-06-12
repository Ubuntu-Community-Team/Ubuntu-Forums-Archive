---
title: "[SOLVED] Error 404 - Gutsy Upgrade"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by shakaran on 2007-09-28
I have Ubuntu Gutsy Gibon Tribe 5

I can't upgrade this packects.

```
aptitude upgrade
```
or
```
apt-get upgrade
```

it's output:

```
Err http://es.archive.ubuntu.com gutsy/main util-linux 2.13-6ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libc6 2.6.1-1ubuntu8
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libc6-i686 2.6.1-1ubuntu8
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main bsdutils 1:2.13-6ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main mount 2.13-6ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-user-guide 2.18.2+svn20070912ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libpam-runtime 0.99.7.1-4ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libpam0g 0.99.7.1-4ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libpam-modules 0.99.7.1-4ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main xkb-data 0.9-4ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libvolume-id0 113-0ubuntu12
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main udev 113-0ubuntu12
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main volumeid 113-0ubuntu12
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main util-linux-locales 2.13-6ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main wpasupplicant 0.6.0+0.5.8-0ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main ubuntu-minimal 1.74
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main apparmor 2.1+993-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main apparmor-utils 2.1+993-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main command-not-found-data 0.2.8ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main command-not-found 0.2.8ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libparted1.7-1 1.7.1-5.1ubuntu8
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main memtest86+ 1.70-3ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main parted 1.7.1-5.1ubuntu8
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main ubuntu-standard 1.74
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main update-manager-core 1:0.78
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gtk2-engines-pixbuf 2.12.0-1ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libgtk2.0-0 2.12.0-1ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libgtk2.0-common 2.12.0-1ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main bluez-gnome 0.14-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main capplets-data 1:2.20.0-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main evince 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libnm-glib0 0.6.5-0ubuntu14
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main evolution 2.12.0-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main evolution-common 2.12.0-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main evolution-plugins 2.12.0-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main f-spot 0.4.0-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libpanel-applet2-0 1:2.20.0.1-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-panel-data 1:2.20.0.1-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-control-center 1:2.20.0-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libgnome-window-settings1 1:2.20.0-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-panel 1:2.20.0.1-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main fast-user-switch-applet 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main python-gtkhtml2 2.19.1-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-app-install 0.4.11-0ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-games 1:2.20.0.1-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-games-data 1:2.20.0.1-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-cards-data 1:2.20.0.1-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gnome-power-manager 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gparted 0.3.3-2ubuntu5
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gstreamer0.10-plugins-good-dbg 0.10.6-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gstreamer0.10-plugins-good 0.10.6-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main gstreamer0.10-esd 0.10.6-0ubuntu4
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main language-selector 0.2.7
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main language-selector-common 0.2.7
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libgtk2.0-bin 2.12.0-1ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libnm-util0 0.6.5-0ubuntu14
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main subversion 1.4.4dfsg1-1ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libsvn1 1.4.4dfsg1-1ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libtotem-plparser7 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libx86-1 0.99-1.2ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/restricted linux-generic 2.6.22.12.15
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/restricted linux-restricted-modules-common 2.6.22.4-12.3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main network-manager 0.6.5-0ubuntu14
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main python-gnome2-extras 2.19.1-0ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/restricted sl-modem-daemon 2.9.10+2.9.9d+e-pre2-5ubuntu3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main totem-xine 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main totem 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main totem-mozilla 2.20.0-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main update-manager 1:0.78
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main update-notifier-common 0.59.6
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main update-notifier 0.59.6
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main usplash-theme-ubuntu 0.17
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/restricted xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-12.3
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main xserver-xorg-video-ati 1:6.7.194-1ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main xserver-xorg-video-nv 1:2.1.5-1ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
Err http://es.archive.ubuntu.com gutsy/main libcompizconfig0 0.5.2+git20070919-0ubuntu2
  404 Not Found [IP: 150.214.5.135 80]
E: Fallo al renombrar http://es.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.13-6ubuntu1_i386.deb a 404 Not Found [IP: 150.214.5.135 80]
```

Please, i need help.

---

### Post by Pumalite on 2007-09-28
The servers might be down for a while. Try later.

---

### Post by oerd on 2007-09-28
HTTP 404 error means that the requested resource (in this case a .deb package) was not found. This usually comes from:

1. Not being connected to the network (maybe cable unplugged or wireless card turned off)
2. The server is down, i.e. does ip 150.214.5.135 (ubuntu.cica.es) respond to a ping? From the shell run ```
ping 150.214.5.135
``` and see if there is a response.
3. A variety of other reasons that don't come to mind :D

see if it's 1 or 2.

---

### Post by jarocooke on 2007-09-28
Probably what happened is that while doing the upgrade, some of the packages were updated on the Ubuntu servers.  If you refresh your package list, then the problem should go away.  I think this is just a occupational hazard of upgrading to a work in progress OS.

---

### Post by shakaran on 2007-09-28
Ok. 

1-The servers NOT are down.
2-My network works fine.
3-Pings answer:

```
shakaran@shakaran:~$ ping 150.214.5.135
PING 150.214.5.135 (150.214.5.135) 56(84) bytes of data.

--- 150.214.5.135 ping statistics ---
143 packets transmitted, 0 received, 100% packet loss, time 142086ms
```

But [http://ubuntu.cica.es/](http://ubuntu.cica.es/) is up in my browser FF. (i dont understand it :confused:)


4-I refresh my list of packages often(many many times), but for many days it has not been working well

5-For example, this line:
```
Err http://es.archive.ubuntu.com gutsy/main util-linux 2.13-6ubuntu1
  404 Not Found [IP: 150.214.5.135 80]
```

I search with browser in this server:
[http://es.archive.ubuntu.com/ubuntu/pool/universe/u/util-linux/](http://es.archive.ubuntu.com/ubuntu/pool/universe/u/util-linux/)

but the package NOT has been uploaded!! In other cases, same.

Please fixed this. It is more important.

---

### Post by oerd on 2007-10-03
Shakaran, did you solve it?
I had the same problem a couple of days ago because the italian mirror i am using got somehow out of sync with the main ubuntu server (i think at least).
I solved by using the main mirror. You can choose the main server in the menu: **System->Administration->Software Sources** then you just choose main server and it refreshes all the package sources.
If you get it done, please mark the thread as solved.

---

### Post by shakaran on 2007-10-04
Tranks oerd, i solve my problem.

---

