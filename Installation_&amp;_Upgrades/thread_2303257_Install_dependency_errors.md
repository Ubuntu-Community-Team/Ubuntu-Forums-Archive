---
title: "Install dependency errors"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by 10kJS on 2015-11-17
I asked this on the Desktop Environments a couple of days ago on no definitive response yet so though there might be some other issues too.  See the image errors trying to install some gnome on 14.04 LTS.  All advice is appreciated though I prefer you be sure or try it on a test install.

---

### Post by kansasnoob on 2015-11-17
10kJS began asking about this on [my Trusty flashback thread]("http://ubuntuforums.org/showthread.php?t=2220264") beginning with [post #63]("http://ubuntuforums.org/showthread.php?t=2220264&page=7&p=13390846#post13390846"). If you look at the attached screenshot you can see that there is a version mismatch for gnome-session-common (it wants to depend on 3.9.90-0ubuntu12 rather than 3.9.90-0ubuntu12.1) which leads me to believe that an upgrade was interrupted at some point.

I've made suggestions to no avail:

[http://ubuntuforums.org/showthread.php?t=2220264&page=7&p=13391060#post13391060](http://ubuntuforums.org/showthread.php?t=2220264&page=7&p=13391060#post13391060)

[http://ubuntuforums.org/showthread.php?t=2220264&page=8&p=13391793#post13391793](http://ubuntuforums.org/showthread.php?t=2220264&page=8&p=13391793#post13391793)

10kJS indicated that I'm not trusted so I can't possibly help any further:

[http://ubuntuforums.org/showthread.php?t=2220264&page=7&p=13391749#post13391749](http://ubuntuforums.org/showthread.php?t=2220264&page=7&p=13391749#post13391749)

Maybe an update/upgrade was interrupted at some point? Or maybe the software sources are somehow messed up? Regardless I can't help as I'm apparently not trusted. Not sure why 10kJS drifted into this sound issue thing:

[http://ubuntuforums.org/showthread.php?t=2220264&page=8&p=13392119#post13392119](http://ubuntuforums.org/showthread.php?t=2220264&page=8&p=13392119#post13392119)

---

### Post by 10kJS on 2015-11-18
[FONT=arial]My install isn't corrupted.  I got the same error with gnome-session on a Live USB.  gnome-session-flashback wasn't available.  Looks like a packaging issue or is not supported on 14.04 LTS.
gnome-panel wasn't available either.[/FONT]

---

### Post by kansasnoob on 2015-11-18
I replied on the [flashback mailing list]("https://mail.gnome.org/archives/gnome-flashback-list/2015-November/thread.html"):

[https://mail.gnome.org/archives/gnome-flashback-list/2015-November/msg00011.html](https://mail.gnome.org/archives/gnome-flashback-list/2015-November/msg00011.html)

At some point you have to follow advice and try to get to the root of the held broken packages.

---

### Post by kansasnoob on 2015-11-18
I had a thought after reading your last mailing list post. The following command is to provide information only. It will not "break" anything. We need to get to the bottom of the version mismatches, so please post the entire terminal output of this command(just copy-n-paste):

```
apt-cache policy alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon
```

This is the output of mine in case someone else wants to compare package versions from a properly updated Trusty (and also to prove I have no intention of purposely breaking things):

```
lance@lance-desktop:~$ apt-cache policy alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon
alacarte:
  Installed: 3.10.0-1ubuntu2
  Candidate: 3.10.0-1ubuntu2
  Version table:
 *** 3.10.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
gir1.2-gconf-2.0:
  Installed: 3.2.6-0ubuntu2
  Candidate: 3.2.6-0ubuntu2
  Version table:
 *** 3.2.6-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
gir1.2-panelapplet-4.0:
  Installed: 1:3.8.0-1ubuntu12.2
  Candidate: 1:3.8.0-1ubuntu12.2
  Version table:
 *** 1:3.8.0-1ubuntu12.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
gnome-applets:
  Installed: 3.5.92-0ubuntu3
  Candidate: 3.5.92-0ubuntu3
  Version table:
 *** 3.5.92-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
gnome-applets-data:
  Installed: 3.5.92-0ubuntu3
  Candidate: 3.5.92-0ubuntu3
  Version table:
 *** 3.5.92-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
gnome-control-center:
  Installed: 1:3.6.3-0ubuntu56.1
  Candidate: 1:3.6.3-0ubuntu56.1
  Version table:
 *** 1:3.6.3-0ubuntu56.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu56 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
gnome-control-center-data:
  Installed: 1:3.6.3-0ubuntu56.1
  Candidate: 1:3.6.3-0ubuntu56.1
  Version table:
 *** 1:3.6.3-0ubuntu56.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu56 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
gnome-media:
  Installed: 3.4.0-1ubuntu2
  Candidate: 3.4.0-1ubuntu2
  Version table:
 *** 3.4.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
gnome-panel:
  Installed: 1:3.8.0-1ubuntu12.2
  Candidate: 1:3.8.0-1ubuntu12.2
  Version table:
 *** 1:3.8.0-1ubuntu12.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
gnome-panel-data:
  Installed: 1:3.8.0-1ubuntu12.2
  Candidate: 1:3.8.0-1ubuntu12.2
  Version table:
 *** 1:3.8.0-1ubuntu12.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
gnome-session:
  Installed: 3.9.90-0ubuntu12.1
  Candidate: 3.9.90-0ubuntu12.1
  Version table:
 *** 3.9.90-0ubuntu12.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.9.90-0ubuntu12 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
gnome-session-flashback:
  Installed: 1:3.8.0-1ubuntu12.2
  Candidate: 1:3.8.0-1ubuntu12.2
  Version table:
 *** 1:3.8.0-1ubuntu12.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
gnome-settings-daemon:
  Installed: 3.8.6.1-0ubuntu11.2
  Candidate: 3.8.6.1-0ubuntu11.2
  Version table:
 *** 3.8.6.1-0ubuntu11.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.8.6.1-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
gstreamer0.10-gconf:
  Installed: 0.10.31-3+nmu1ubuntu5
  Candidate: 0.10.31-3+nmu1ubuntu5
  Version table:
 *** 0.10.31-3+nmu1ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
indicator-applet-complete:
  Installed: 12.10.2+14.04.20140403-0ubuntu1
  Candidate: 12.10.2+14.04.20140403-0ubuntu1
  Version table:
 *** 12.10.2+14.04.20140403-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
libgnome-media-profiles-3.0-0:
  Installed: 3.0.0-1ubuntu2
  Candidate: 3.0.0-1ubuntu2
  Version table:
 *** 3.0.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
libgoa-backend-1.0-1:
  Installed: 3.10.3-0ubuntu1
  Candidate: 3.10.3-0ubuntu1
  Version table:
 *** 3.10.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
libpanel-applet-4-0:
  Installed: 1:3.8.0-1ubuntu12.2
  Candidate: 1:3.8.0-1ubuntu12.2
  Version table:
 *** 1:3.8.0-1ubuntu12.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
metacity:
  Installed: 1:2.34.13-0ubuntu4.1
  Candidate: 1:2.34.13-0ubuntu4.1
  Version table:
 *** 1:2.34.13-0ubuntu4.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:2.34.13-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
notification-daemon:
  Installed: 0.7.6-1
  Candidate: 0.7.6-1
  Version table:
 *** 0.7.6-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
lance@lance-desktop:~$ 

```

---

### Post by 10kJS on 2015-11-19
[FONT=arial]Was resolved by Dmitry on gnome-flashback-list.  My install was not corrupted.  I never saw anywhere that trusty-updates was needed:

Run command:  software-properties-gtk 
Select:  "Updates" tab 
Select:  "Recommended updates (trusty-updates)"
[/FONT][FONT=arial]Run command:  sudo apt-get install gnome-session-flashback[/FONT]

---

### Post by kansasnoob on 2015-11-19
That would explain the mismatched package versions.

---

