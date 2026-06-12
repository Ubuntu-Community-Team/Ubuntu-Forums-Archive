---
title: "ffado on Intrepid beta"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pointfive on 2008-10-23
Sorry if this should be posted elsewhere. I've been trying to get ffado (also beta) working on Intrepid. I've followed [this installation guide]("http://www.ffado.org/?q=node/613"), and was able to compile the drivers, but when I attempt to run ffadomixer, I get a messagebox saying, "The connection to FFADOs DBus service could not be established. Probably you didn't start the ffado-dbus-server. Should I try this now?"

If I click yes, I get the following output (if run in a terminal):

```
===========================================================
ERROR: Could not communicate with the FFADO DBus service...
===========================================================


01410456750:  (ffado-dbus-server.cpp)[ 249] main: FFADO Control DBUS service
01410456909: Debug (ffado-dbus-server.cpp)[ 251] main: verbose level = 4
01410456925: Debug (ffado-dbus-server.cpp)[ 252] main: Using ffado library version: libffado 1.999.36-

01410456935:  (ffado-dbus-server.cpp)[ 255] main:  Discovering devices...
01410457565: [COLOR="Red"]Error (ieee1394service.cpp)[ 129] detectNbPorts: Could not get libraw1394 handle.[/COLOR]
01410457582: [COLOR="Red"]Fatal (devicemanager.cpp)[ 145] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?[/COLOR]
01410457594: [COLOR="Red"]Error (ffado-dbus-server.cpp)[ 262] main: Could not initialize device manager[/COLOR]
01410457852: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns

```

Then it hangs. If I do a keyboard interrupt, I get:

```
^CTraceback (most recent call last):
  File "/usr/local/bin/ffadomixer", line 327, in <module>
    time.sleep( 1 )
KeyboardInterrupt

```

I've done searches for those errors, but no luck

I'm on a Dell Inspiron using a firewire expresscard, attempting to connect to a Focusrite Saffire LE. I've tried this with everything plugged in and with nothing plugged in, the result is always the same (makes sense, since the error seems to be with the drivers starting up in the first place).

Any help will be greatly appreciated. I've been banging my head against this for awhile. Thanks.

---

