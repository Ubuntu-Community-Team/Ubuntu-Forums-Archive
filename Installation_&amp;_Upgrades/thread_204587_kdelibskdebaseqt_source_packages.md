---
title: "kdelibs/kdebase/qt source packages?"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by bsander on 2006-06-27
I want to add a patch ([this one](http://ktown.kde.org/~seli/xinerama/)) to KDE 3.5.3 as provided by kubuntu dapper. Now I assume that kubuntu patched its version of KDE already for other goodness so I need the source of that to add this patch and recompile. To be precise I need the sources of Qt3, kdelibs (3.5.3) and kdebase (3.5.3). Does anyone know where I can find those? Or is my assumption incorrect and can I just use the standard sources of these packages as provided by KDE and Trolltech?

---

### Post by gborzi on 2006-06-27
This command > sudo apt-get source <package name> downloads the sources of the desired package. You need to have some knowledge on packaging to build the binary package from the sources, adding the patch. So, you may want to read the Debian New Maintainers' Guide, i.e.
> sudo apt-get install maint-guide

---

### Post by bsander on 2006-06-27
Thanks! I'm building Qt as we speak, hope this is gonna work :)

---

