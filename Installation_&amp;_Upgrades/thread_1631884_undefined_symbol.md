---
title: "undefined symbol"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by gasrine on 2010-11-27
Hi,
I've compiled a program on [URL="http://www.linuxquestions.org/questions/#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]ubuntu[/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]  with the command line "make python" but the problem comes when I tried to use it and  exactly after the command line "from libpy import *", the message that  appears is such 

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "libpy/knit.py", line 28, in <module>
    import _knit
ImportError: libpy/_knit.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE

I don't know if it's a problem with the compilation or linking or other issues.
I'll be thankful if someone could help me

---

