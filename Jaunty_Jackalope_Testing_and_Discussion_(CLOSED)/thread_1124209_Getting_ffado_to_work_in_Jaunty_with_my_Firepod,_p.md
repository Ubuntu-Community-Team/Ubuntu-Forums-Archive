---
title: "Getting ffado to work in Jaunty with my Firepod, permission troubles"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sumpm1 on 2009-04-13
I am desperately trying to get my audio interface to work with Ubuntu, and I had my hopes set that Jaunty would be easier to get Ffado running with jack for recording. I have installed liffado, libjack... When even trying to run the ffado mixer I get permission errors, I need to add myself to the audio group, as explained in many threads and guides. I am having permission troubles when trying to even run the ffado mixer or bus server. I get the following error:

```
dave@dave-desktop:~$ ffado-dbus-server &
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

03755246005:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
03755246650: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
03755246666: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
03755246671: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
03755246703: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns
[1] 7728

```

And most guides say to run

```
sudo nano /etc/udev/rules.d/40-permissions.rules
```

to check your "raw1394 group." But this file does not seem to exist on my installation. What can I do to see what group raw1394 requires me to be in?

Thanks

---

