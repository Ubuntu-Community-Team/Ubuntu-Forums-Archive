---
title: "beagle killed"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by alex1974 on 2007-05-30
Need help again!

Beagle and tomboy don't run anylonger. It seems I've broken something
The terminal shows:

[COLOR="DarkSlateGray"]alex@alex-leisser:~$ beagle-search --help

** (/usr/lib/beagle/Search.exe:8464): WARNING **: The following assembly referenced from /usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f/gtk-sharp.dll could not be loaded:
     Assembly:   atk-sharp    (assemblyref_index=4)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f).


** (/usr/lib/beagle/Search.exe:8464): WARNING **: Could not load file or assembly 'atk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
The entry point method could not be loaded[/COLOR]

The same result when I run tomboy --help

Any guess what I did wrong?

Thanks,
Alex

---

