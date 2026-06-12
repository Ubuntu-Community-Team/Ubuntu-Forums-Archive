---
title: "After upgrading to dapper, GNOME can't create a session"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by batkins on 2006-06-14
I just upgraded to Dapper, and now when I log into GNOME, I get an error that says "I could not start your session and so I have started the failsafe xterm session.  Windows have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner."  If I type gnome-session into the xterm it gives me, everything comes up properly.

This happens even with newly-created languages.  The only way to get in is to have GDM use the GNOME Failsafe session type.

I've tried deleting .ICEAuthority and .gnome2/session to no avail.

What can I do to fix this?

Here are the contents of .xsession-errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bill"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator

---

### Post by catlett on 2006-06-14
There are a couple of things you scould try. You could reconfigure x and see if that helps ```
sudo dpkg-reconfigure xserver-xorg
``` You could try uninstalling then re-installing gdm and hope the new install configures correctly. ```
sudo aptitude update
``````
 sudo aptitude remove gdm 
``````
sudo aptitude install gdm
``` I would start with that and see what happens. I would reconfigure first and reboot. If nothing, uninstall re-install reboot. mIf still nothing I would uninstall gnome altogether and then re-install. I would think that it would reconfigure correctly. Sometimes the upgrades don't hold the previous configuration well and it works better to set up your desktop by installing instead of updating. ```
sudo aptitude remove ubuntu-desktop
``` ```
sudo aptitude install ubuntu-desktop
```

---

### Post by batkins on 2006-06-23
bump?

---

### Post by andrem on 2007-01-28
I know this thread is old, but have you managed to solve this problem? It is happening exactly the same thing to me.

---

### Post by batkins on 2007-01-28
I had to do a clean install of Dapper.

Happily, I don't have to worry about these kinds of things anymore, as OS X takes good care of me.

---

