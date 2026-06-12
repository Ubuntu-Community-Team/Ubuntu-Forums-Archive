---
title: "Install bonks on G4 PowerBook (Titanium)"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by dtheobald on 2006-09-04
Hey all --

I have been told that Ubuntu is a good choice for the PPC, but I'm hitting a brick wall on my 500 MHz G4 TiBook (1 Gb RAM and 20 Gb drive). I was able to successfully burn the .iso to CD and boot with it. I get through the initial brown ubuntu screen ("Loading essential drivers ... ok", "Mounting root filesystem ... ok",  etc.). I also get through a terminal-like screen that loads drivers and stuff and ends with "Loading Gnome display manager ...". This is where the install bonks. I get the pretty ubuntu screen and the music, but I'm immediately presented with the following three X-window error screens:

Nautilus can't be used now, due to an unexpected error.
-> Show more details
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

Also:

There was an error starting the GNOME Settings Daemon.
Some things such as themes, sounds, or background settings may not work correctly.
The Settings Daemon restarted too many times.
The last error message was:
System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0
GNOME will still try to restart the Settings Daemon next time you log in.

and:

There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.

Any ideas or am I just hosed?

Thanks,

Douglas

---

### Post by linear on 2006-09-04
The alternate install CD works better for a lot of people. You might want to give it a try.

---

### Post by dtheobald on 2006-09-05
Hey thanks, that was the ticket, I'm writing from Ubuntu. Very nice. Now if I could just get it to recognize my wide screen ...

---

