---
title: "can't VNC after upgrade"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by daveh0 on 2010-01-09
so i'll start off by saying that I am accessing the box via SSH It is physically in a location where it would be extremely difficult to connect to a monitor/keyboard/mouse. So I'd like to be able to resolve my issue from the command line....

I just upgraded to Ubuntu 8 (Hardy Herron). Before the upgrade, I was able to VNC to this box from my Windows machine and access the Gnome desktop without problems.

It seems that with this upgrade, the way vncserver is started has changed as I can tell it is not running when I reboot. So I started it manually:

```

daveh0@babybird:~$ sudo vncserver

New 'babybird:2 (root)' desktop is babybird:2

Starting applications specified in /home/daveh0/.vnc/xstartup
Log file is /home/daveh0/.vnc/babybird:2.log

```

Now I can connect via VNC from my Windows box but I get some weird version of the X desktop - see attached screen shot.



Can anyone tell me how I can get vncserver to start on startup AND how to configure it to show me my Gnome desktop when I connect via VNC?

Thanks,

-dave

---

