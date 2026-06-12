---
title: "Following update can't get past login screen"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by skiloup on 2010-10-17
I had a single user account on my lucid install.  I upgraded to maverick and can't login as my user.  At the gdm it accepts my password, flashes a blank screen then returns me to the gdm.

I can login to the box via ssh, and also login from a different tty but I can't start x. ~/.xsession-errors doesn't tell me much useful.
```

gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
gnome-session: Fatal IO error 4 (Interrupted system call) on X server :1.0.
Window manager error: Unable to open X display :1.0

```

/var/log/Xorg.0.log doesn't seem to have any that helps either.

If I create a new user, it can login from the gdm and start x without any problems.

Anybody have any ideas?

---

### Post by franklamoureux on 2010-10-20
I'm having a similar issue. The difference is that I can login but the crash of X Server happens randomly after I logged in. 5 minutes, 10 minutes, while browsing or running the Video testing. Can't find a single pattern to reproduce every time.
Same thing, nothing useful in X.org.log. Newly created user does not causes any problems. Where are the personal configuration for anything theme/X/personalization related?

~/.xsession_errors contains the following:
```

gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
ICE default IO error handler doing an exit(), pid = 2082, errno = 11
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

[01mHP Linux Imaging and Printing System (ver. 3.10.6)[0m
[01mSystem Tray Status Service ver. 2.0[0m

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

ICE default IO error handler doing an exit(), pid = 2085, errno = 11
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
--log-level=debug: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

[01mHP Linux Imaging and Printing System (ver. 3.10.6)[0m
[01mSystem Tray Status Service ver. 2.0[0m

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

The application 'gksu' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

---

### Post by franklamoureux on 2010-10-27
Well, after fiddling around I resolved the X server crash of that migrated user with one of the following (sorry, don't know which one worked).

- Installed all recent updates (Software Update)
- Manually uninstalled any package related to nvidia using Synaptic Package Manager
- Deleted all that was in ~/.themes/
- Ran the following commands
  - sudo apt-get --purge autoremove && sudo apt-get clean
  - sudo apt-get --reinstall install nvidia-glx-185
  - sudo apt-get --reinstall install nvidia-185-modaliases
  - Re-activate the nvidia-current driver

And of course lots of reboot to test the changes. Hope this helps.

---

