---
title: "tomboy killed"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by alex1974 on 2007-05-30
I need help!

I used tomboy and found it very useful. But suddenly I have troubles. It is not working. Nothing happens. In the terminal I get:

[COLOR="DimGray"]alex@alex-leisser:~$ tomboy --help

** (/usr/lib/tomboy/Tomboy.exe:7388): WARNING **: The following assembly referenced from /usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f/gtk-sharp.dll could not be loaded:
     Assembly:   atk-sharp    (assemblyref_index=4)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f).


** (/usr/lib/tomboy/Tomboy.exe:7388): WARNING **: Could not load file or assembly 'atk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'atk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.[/COLOR]

I tried to install gtk-sharp and gtk-sharp2 but that didn't solve it.
What now?

Thanks for the help,
Alex

---

