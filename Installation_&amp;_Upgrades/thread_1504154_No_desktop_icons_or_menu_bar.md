---
title: "No desktop icons or menu bar?"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by whiskeyhotel on 2010-06-07
Hello,

I just installed Ubuntu 10.04. I'm a first time user. when i boot up computer, I can choose Ubuntu, and it starts up, but there are no desktop icons, no menu bar (?). I'm able to right click and create folders and files, but that's about it. any ideas? Installed on an older pc running windows xp

thanks

---

### Post by arrange on 2010-06-07
Do you see something like this (without the icon)?
[IMG]http://ubuntulady.files.wordpress.com/2010/03/standard.png?w=500[/IMG]

Or is there only the background and no panels or icons at all?
Are you using *Wubi* (Ubuntu installed within XP) or classic installation on an extra partition on the disk?

---

### Post by whiskeyhotel on 2010-06-07
There is only the background with no panels at all. It was the classic install on extra partition.

---

### Post by arrange on 2010-06-07
Could you please open up a [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and type```
ps aux | grep gnome
```(to see what gnome processes are running)
and post the output here?

It may also help if you uploaded/attached the *~/.xsession-errors* file.

---

### Post by whiskeyhotel on 2010-06-07
Is there anyway to access terminal by right clicking on desktop, because I have nothing else to click on

---

### Post by arrange on 2010-06-07
Haha, sorry, I forgot :)

Right click, *Create launcher*, and in the *Command* field type *gnome-terminal* (*Name* doesn't matter). Click OK. Then you should see a new icon on the desktop.

---

### Post by whiskeyhotel on 2010-06-07
Here it is:

whiskeytown@whiskeytown-desktop:~$ ps aux | grep gnome
root       724  0.0  0.5  20488  2880 ?        Sl   12:21   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
1000      1145  0.0  0.4  23980  2112 ?        Sl   12:21   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
1000      1163  0.0  1.2  25908  6452 ?        Ssl  12:21   0:00 gnome-session
1000      1197  0.0  0.0   3276   288 ?        Ss   12:21   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
1000      1200  0.0  0.1   3376   688 ?        S    12:21   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
1000      1211  0.0  1.6  88932  8604 ?        Ss   12:21   0:05 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
1000      1223  0.0  1.4  20032  7552 ?        S    12:21   0:00 gnome-power-manager
1000      1224  0.0  1.1  18392  5920 ?        S    12:21   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
1000      1227  0.0  2.6  40048 13648 ?        S    12:21   0:04 gnome-panel
1000      1278  0.0  0.6  17804  3192 ?        Ss   12:21   0:00 gnome-screensaver
1000      1285  0.2  2.5  39384 12756 ?        S    12:21   0:19 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
1000      1287  0.0  2.0  37188 10408 ?        S    12:21   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=24
1000      1295  0.0  2.4  31952 12424 ?        S    12:21   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=29
1000      1299  0.0  1.6  23096  8476 ?        S    12:21   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=41
1000      1314  0.0  1.3  18912  7016 ?        S    12:21   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
1000      2902  0.2  2.2  35396 11488 ?        S    14:37   0:02 gnome-desktop-item-edit --create-new /home/whiskeytown/Desktop
1000      3026  5.8  2.4  44540 12436 ?        Sl   14:51   0:00 gnome-terminal
1000      3027  0.0  0.1   1980   704 ?        S    14:51   0:00 gnome-pty-helper
1000      3048  0.0  0.1   3320   856 pts/0    S+   14:51   0:00 grep --color=auto gnome
whiskeytown@whiskeytown-desktop:~$

---

### Post by tmette on 2010-06-07
Does your mouse go off the screen like there is more there but you can't see it?  Try to move your mouse all the way in the upper-left corner and click.  Your resolution might be messed up.

---

### Post by whiskeyhotel on 2010-06-07
My mouse doesn't go off the screen. I'm viewing eveything thats being displayed

Edit: The mouse does go off the screen on the bottom, but not the top when viewing desktop.

---

### Post by arrange on 2010-06-07
*gnome-panel* is running, so it must be somewhere :)

_Try any/all of these:_ (if they don't work, change the values back to default ones)
Run *gnome-appearance-properties*. Change theme and/or switch *visual effects* to *none*.
Run *gnome-display-properties*. Try changing the resolution or monitor.
You can also stop the *gnome-panel* process; it should respawn automatically and may appear: ```
killall gnome-panel
```

You could also provide a screenshot, maybe it will look familiar to someone - run *gnome-screenshot*.

---

### Post by whiskeyhotel on 2010-06-07
Thanks, I think progress is being made!

I ran Run [I]gnome-appearance-properties and switched themes and the  panels at the bottom showed up.

[/I]stopping the *gnome-panel* process with code killall genome-panel gave me panels at the top, clock, etc.

Am i supposed to have default icons on the desktop?
[IMG]http://ubuntuforums.org/home/whiskeytown/Desktop/Screenshot.png[/IMG]

---

### Post by SlidingHorn on 2010-06-07
A fresh install (as far as I remember) does not have any icons on the desktop.  They'll show up if you create .desktop files for them or if you mount another filesystem, etc.

---

### Post by arrange on 2010-06-08
No default icons :) You can easily create them by dragging them from a folder or *Applications* menu etc

---

