---
title: "Ghostscript and GSView on Linux"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2007-09-14
Hello, I'm running Dapper-64. The Synaptic apt-get program searches and finds variants on GhostScript and comments their flavors of GhostScript are GNU license whereas the original GhostScript is not. Well, the latest and greatest GhostScript is GPL (Aug.2007, don't make commercial software with it). You download it from the university that started the project. The sources files for GhostScript do build on Ubuntu using the defaults. The console-mode part of GhostScript does work at that point.

I could * NOT* build the GUI graphic viewer called GSView. I could however use the RedHat RPM and alien the .deb which did install. GSView fires up from console and then fails to read a PDF or postscript file. The ReadMe.htm for GSView is hidden in the targ.gz. It reads:

```
**X11/Unix**

Copy gsview, gsview-help, epstool and pstotext to a directory on your search path. Copy
gvx*.htm to the directory /usr/share/doc/gsview-N.N. Copy printer.ini to directory 
/etc/gsview. GSview stores configuration information in $HOME/.gsview.ini.

You must have the shared object version of Ghostscript 7.04 - 9.19, which should be included
in recent GNU/Linux distributions. If you don't have the ghostscript shared object, you
must first install Ghostscript, then the additional shared object files. To build the 
ghostscript shared object files, use './configure ; make so' 

```

Questions:
1. "A directory on my search path" is that Home??? What directory?
2. The Shared Object mentioned in the 2nd paragraph, does that suggest I have to reBuild?

Until SVG becomes a reality, I was exploring PostScript with Python code and I need the GUI viewer as a reference.

3. Is there another GUI viewer that will hook up to GhostScript if I can't make GSView connect?

Thanks, *buntu people. You've helped me so much in the past.

---

