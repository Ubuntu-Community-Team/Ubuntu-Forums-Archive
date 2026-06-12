---
title: "Problems when installing ChScite"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by kinemagician on 2007-11-09
I tried to install ChScite 
([http://chscite.sourceforge.net/](http://chscite.sourceforge.net/))
but I get the following error 
--------------------------------------------------------------
/home/ettore/chscite-1.5.5/scintilla/gtk> make
g++ `pkg-config --cflags gtk+-2.0` -DNDEBUG -Os -Wall -Wno-missing-braces -Wno-char-subscripts -DGTK -DSCI_LEXER -I ../include -I ../src  -c ../src/DocumentAccessor.cxx
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
/bin/sh: g++: not found
make: *** [DocumentAccessor.o] Error 127
----------------------------------------------------------------------------

I am running Ubuntu 7.10.
Can you help me?

Thanks,
Ettore

---

