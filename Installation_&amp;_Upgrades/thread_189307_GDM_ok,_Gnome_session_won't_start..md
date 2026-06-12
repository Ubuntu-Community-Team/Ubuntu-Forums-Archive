---
title: "GDM ok, Gnome session won't start."
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by kiwibird on 2006-06-05
I just logged in after an update, using GDM, then I got an error message saying 
"[I]I could not start your session and so I have started the failsave xterm 
session. Windows now have focus only if you have your cursor above 
them. To get out of this mode type 'exit' in the window in the upper 
left corner[/I]", 
and was put into a single xterm-window. 

Also, I got some errors in the update process; I used update-manager, got done with downloading&installing, then on cleanup I got a fatal error:

```
Traceback (most recent call last):

  File "/tmp/tmpNZAYzF/dapper", line 28, in ?

  File "/tmp/tmpNZAYzF/DistUpgradeControler.py", line 513, in run

  File "/tmp/tmpNZAYzF/DistUpgradeControler.py", line 503, in dapperUpgrade

  File "/tmp/tmpNZAYzF/DistUpgradeControler.py", line 364, in doPostUpgrade

  File "/tmp/tmpNZAYzF/DistUpgradeControler.py", line 64, in openCache

  File "/tmp/tmpNZAYzF/DistUpgradeCache.py", line 18, in __init__

  File "/tmp/tmpNZAYzF/DistUpgradeConfigParser.py", line 10, in getlist

  File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
    raise NoSectionError(section)

NoSectionError: No section: 'Distro'

```

Is this related? What should I do in response to these errors? I also noticed a lot of programs wanted to start gtk dialogs (I think) during install, but weren't allowed to, is that normal?


Starting failsafe Gnome gives me a background and workspaces, but the top and bottom spaces are useless - nothing happens when I click anything there. (Although, while .Trash was not empty, hovering over the trash icon gave me constantly increasing numbers of items, weird.)

The power management gave me this error message on startup: 
"[I]This program cannot start until you start the dbus session service.
This is usually started automatically in X or gnome startup when you start a new session.[/I]"

Here's the cat of my .xsession-errors:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kiwibird"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
```

---

### Post by ajft on 2006-06-05
I seem to have a similar problem.  A machine that some months ago was upgraded from Debian to Ubuntu 5.10, then last weekend I upgraded from 5.10 to 6.06.

When running Ubuntu 5.10, dbus worked, gnome-session worked, ssh-agent worked.

After the upgrade I get no gnome-session, ssh-agent isn't loaded, dbus isn't loaded and I get the single xterm and no window manager.  I can then manually run "gnome-session" and get my gnome session back!

---

### Post by kiwibird on 2006-06-06
Do you know how to start dbus so as to let power management &c run? (Just wondering as a temporary fix, I tried just running "dbus-daemon --session &" before gnome-session, but that didn't help.)

Anyone out there got a clue what to do? What files are related? It's weird how it persists after completely reinstalling ALL of the ubuntu-desktop packages, plus all of X ("apt-get remove --purge x11-common"). My /etc/X11-folder was pretty much empty (no Xsession.d, nor xorg.conf, nor Xsession.options). Also, I noticed that on reinstalling ubuntu-desktop, the Xsession.d-folder has a lot more scripts in it, which seems a bit wrong to me (shouldn't they have been put there on my update to dapper?). 

EDIT: had to run "dbus-launch gnome-session" to get power-management and such stuff. Apparently that's what the script that launches X (or something) should be saying. I have no idea what script this is in Ubuntu, nor why it doesn't remove itself when I do my purges.

---

