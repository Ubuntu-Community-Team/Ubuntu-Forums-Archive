---
title: "installing f-spot"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by jclemon on 2005-07-11
i installed f-spot using the synaptic package manager and then did a sudo apt-get dist-upgrade when upgrading 26 things failed through the updater. i got everything updated and when i go to launch f-spot, it appears in the window list panel as "starting f-spot photo album" but no window appears, then the entry disappears from the panel after a few seconds.

when i run f-spot from the terminal i get this output:

$ f-spot

** (/usr/lib/f-spot/f-spot.exe:8015): WARNING **: _wapi_timestamp_exclusion: Breaking a previous timestamp

** (/usr/lib/f-spot/f-spot.exe:8015): WARNING **: _wapi_timestamp_exclusion: Breaking a previous timestamp

** (/usr/lib/f-spot/f-spot.exe:8015): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=7)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:8015): WARNING **: The class Gnome.Program could not be loaded, used in /usr/lib/f-spot/f-spot.exe (token 0x0100012e)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object

thanks for the help

---

### Post by varunus on 2005-07-12
Install the packages libgnome-cil and libgnome2-cil.

Good luck.  I have fspot working; its a good idea to install all the packages beagle needs from the Beagle Ubuntu howto, and then install fspot.

---

