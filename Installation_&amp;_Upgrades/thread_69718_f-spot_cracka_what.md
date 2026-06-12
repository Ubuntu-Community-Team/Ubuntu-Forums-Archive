---
title: "f-spot cracka what?"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by edm00se on 2005-09-27
So I get the bright idea to try installing f-spot. Took some doing, but I finally was able to install it. While it is currently on my machine, there's this slight problem of it not running. I ran it from terminal to give people who know more than I the oh-so fun, following output:

> eric@RabbitHole:~$ f-spot

** (/usr/lib/f-spot/f-spot.exe:8283): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=7)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:8283): WARNING **: The class Gnome.Program could not be loaded, used in /usr/lib/f-spot/f-spot.exe (token 0x0100012e)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object


  All help is appreciated.

---

