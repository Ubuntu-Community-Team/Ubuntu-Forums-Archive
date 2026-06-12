---
title: "winds (snap app: rss feeds) won't run: Failed to load module &quot;canberra-gtk-module&quot;"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by zachalexy on 2018-10-24
Hi, having problems with running winds, newly installed:

zach@ubuntu-ws:~$ snap install winds
winds 2.3.1 from GetStream.io (getstream-io&#10003;) installed

zach@ubuntu-ws:~$ winds

Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: invalid attribute 'translate'

snapd running and all snaps functioning, except winds :-(

zach@ubuntu-ws:~$ snap list
Name                  Version                  Rev   Tracking  Publisher      Notes
communitheme          0.1                      1273  stable    didrocks       -
core                  16-2.35.4                5662  stable    canonical&#10003;     core
glances               2.11.1                   5     stable    nicolargo      -
gnome-3-26-1604       3.26.0                   74    stable    canonical&#10003;     -
gnome-calculator      3.30.0                   238   stable    canonical&#10003;     -
gnome-characters      3.29.91                  124   stable    canonical&#10003;     -
gnome-logs            3.30.0                   45    stable    canonical&#10003;     -
gnome-system-monitor  3.30.0                   57    stable    canonical&#10003;     -
gtk-common-themes     0.1                      701   stable    canonical&#10003;     -
spotify               1.0.92.390.g2ce5ec7d-18  22    stable    spotify&#10003;       -
winds                 2.3.1                    83    stable    getstream-io&#10003;  -



Already installed all the canberra-gtk-modules, nothing seems to help. Running 18.10 Cosmic Cuttlefish.

All was fine at 18.04.

Any help, much appr. Zach

---

### Post by gloonie2 on 2018-11-12
I have a similar problem. fontconfig issues and a blank screen opens.

---

