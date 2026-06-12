---
title: "Fresh install - VERY broken gnome"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Ford Flox on 2006-06-02
I've just finished the install using the "alternative" install cd. The installation went well, but when logging in to the desktop nothing will start. I just get a whole bunch of error dialogs, mostly from applets that wouldn't start ("do you want to disable this applet", etc). 

In particular gnome settings daemon is having trouble starting, due to the following: System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0.

I could at least get a gnome-panel the first time, but now I get nothing but the brown wallpaper and a few dialogs, notable the one from gnome settings daemon.

I have checked the cd - it appears to be fine. I'm installing on an ibook G4.

---

### Post by iduas on 2006-06-05
I performed an upgrade  with the alternate CD and have the same problem. The errors I get are:

> The Application "gnome-panel" has quit unexpectedly

and

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in.

I have tried deleting .gnome files in my home folder, and searched for ideas in google. I think the first error I got was from the mixer applet, which has gone since I specified the emu10k1 module should be loaded.

System is AMD-K6 II with NVIDIA RIVA TNT2.

---

### Post by themunkee on 2007-03-07
I believe it might have to do with orbit. Try the following:

```
rm /tmp/orbit-*username*
```

---

