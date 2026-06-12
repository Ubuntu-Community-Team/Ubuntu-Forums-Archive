---
title: "Errors on bootup of Edgy after upgrade"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2006-12-20
I have just upgraded from Dapper to Edgy.  On my first boot into the new system I got this error window:

"You have either an install problem or you are out of disc space."

The ~/.xsession-errors file gives this information:
[quote]
/etc/gdm/Presession/Default: Registering your session with wtmp and utmp

/etc/gdm/Presession/Default: Running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/ :0.xservers" -h""-l ":0" "bob"

/etc/gdm/xsession: Beginning session setup...

/etc/x11/xsession.d/39keytouch.acpid: 2: syntax error: "&" unexpected
[unquote]

I have completely uninstalled the keytouch program, but when I reboot the exact same error message appears.  I have several versions of Dapper still on my system (put there through the automatic updates) so conceivably I may be running out of room.  I think I reserved a 5gb partition for the os when I first set up Ubuntu.  If this is the problem, how do I get rid of these no outdated versions?

The next thing I tried was booting into safe mode, but then I got this message:

[quote]
There was an error starting Gnome settings daemon.
Last error message was:
Unable to determine the address of the message bus.
[unquote]

Can someone give me step-by-step instructions on how to tackle this problem?  I am fairly new to Linux but not to computers.  I don't mind editing scripts or other files as long as I know what I am doing.

TIA,
Bob

---

