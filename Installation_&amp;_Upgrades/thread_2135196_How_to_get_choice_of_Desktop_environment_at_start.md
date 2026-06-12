---
title: "How to get choice of Desktop environment at start?"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2013-04-13
I have 13.04 installed with [gnome-fallback]("http://ubuntuforums.org/showthread.php?t=2113480&p=12601506#post12601506")

and writing in the poll thread linked above i thought why not try another one; so have installed [Mate]("http://www.itworld.com/software/351107/install-mate-16-desktop-ubuntu-1304") and that went fine


Now my question is how do i pick it at startup   [**no options** are given me at any point]


I recall having written /etc/xdg/autostart/gnome-settings-daemon.desktop

> [Desktop Entry]Type=Application
Name=GNOME Settings Daemon
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
OnlyShowIn=GNOME;Unity;
NoDisplay=true
X-GNOME-Autostart-Phase=Initialization
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-settings-daemon

so that it would pick gnome-fallback each time automatically; now i see this page [here]("http://blog.lifebloodnetworks.com/?p=1253") shows how to fix it so Mate is the choice

thus

> [COLOR=#666666][FONT=monospace][Desktop Entry][/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]Type=Application[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]Name=Mate Settings Daemon[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]Exec=/usr/bin/mate-settings-daemon[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]OnlyShowIn=MATE;[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]NoDisplay=true[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]X-GNOME-Autostart-Phase=Initialization[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]X-GNOME-Autostart-Notify=true[/FONT][/COLOR]
[COLOR=#666666][FONT=monospace]X-GNOME-AutoRestart=true[/FONT][/COLOR]


**But **i do not want fixed Mate; i just want the option to try it out and probably will return to my current setup   unless it is amazing


now fiddling with /etc/xdg/autostart/gnome-settings-daemon.desktop

can be a dicey business i am sure

so please what do i need to write in the file to be given a choice at startup?

Please only replies from folks who really know about this


PS if there is another route not with /etc/xdg/autostart/gnome-settings-daemon.desktop  will be glad to hear about that too

---

### Post by deadflowr on 2013-04-13
All of the DEs listed in the login screen are listed in /usr/share/xsessions, if that helps.

---

### Post by shantiq on 2013-04-13
thanx D it yields

> /usr/share/xsessions$ ls
gnome.desktop  gnome-fallback-compiz.desktop  gnome-fallback.desktop  mate.desktop  ubuntu.desktop  XBMC.desktop





so i see what is there but it still looks as if 

[COLOR=#000000]/etc/xdg/autostart/gnome-settings-daemon.desktop    is where the entries have to be modified somehow[/COLOR]

---

