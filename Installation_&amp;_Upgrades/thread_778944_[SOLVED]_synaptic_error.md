---
title: "[SOLVED] synaptic error"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by robertchahine on 2008-05-02
i want to remove the swfdec plugin of mozilla and install the gnash swf plugin.
so i remove it from synaptic and install the gnash plugin.
but here the error:
```

Setting up mozilla-plugin-gnash (0.8.2-0ubuntu3) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/xulrunner-flashplugin corrupt: priority /usr/lib/swfdec-mozilla/libswfdecmozilla.so 
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Setting up swfdec-mozilla (0.6.0-2ubuntu1) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/xulrunner-flashplugin corrupt: priority /usr/lib/swfdec-mozilla/libswfdecmozilla.so 
dpkg: error processing swfdec-mozilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
 swfdec-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
i changed once the xulrunner-flashplugin with gksudo gedit.
but i rechanged again to the default, so nothing changed.


everytime i want install something, it works great and install everything but i keep having this error.
so what to do?

---

### Post by robertchahine on 2008-05-02
i don't know if i'm going to use opera!!!!?
but i should first fix this error to keep on firefox

---

### Post by robertchahine on 2008-05-02
i'm confused between opera and FF3 both are fast.

FINALLY IT'S >>>>>>>>SOLVED<<<<<<<<<<

i reconfigured the xul-runnerflashplugin and it wasn't as default so i add some line and it worked like a charm.
i think i'm going back to FF3

---

