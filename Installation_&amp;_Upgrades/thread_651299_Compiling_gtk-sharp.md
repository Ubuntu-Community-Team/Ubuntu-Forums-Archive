---
title: "Compiling gtk-sharp"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by brk3 on 2007-12-27
I've being trying to compile gtk-sharp 2.8.4 so I can then compile the latest monodevelop.
The configure script runs fine but the make fails with this error:

** (/usr/local/lib/mono/1.0/mcs.exe:17810): WARNING **: The following assembly referenced from /home/paul/tmp/gtk-sharp-2.8.4/gnome/gnome-sharp.dll could not be loaded:
     Assembly:   art-sharp    (assemblyref_index=4)
     Version:    2.8.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/paul/tmp/gtk-sharp-2.8.4/gnome/).

Why can't it find this assembly, isn't it part of the gtk-sharp package I'm trying to compile? If anyone has sucessfully compiled gtk-sharp could you please give me a few tips.
Thanks

---

