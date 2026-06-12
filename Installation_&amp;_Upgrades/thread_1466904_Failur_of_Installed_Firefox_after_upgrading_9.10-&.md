---
title: "Failur of Installed Firefox after upgrading 9.10-&gt;10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by csevcik on 2010-04-30
I just upgraded my HP Pavilion (2 AMD 64 bit processors, running Ubuntu 64) all in one desktop computer from 9.10 to 10.4. Seems to be working fine except for Firefox. When I run the Firefox installed by the upgrade it does not run. Firefox 3.6.3 downloaded from Mozilla (installed in /opt/firefox) runs fine (is what I am using right now). Here is what I get by typing firefox in my terminal window:

> $ firefox
NPP_GetValue 1
NPP_GetValue 2
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libxul.so [/usr/lib/mozilla/plugins/libxul.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libmozjs.so [/usr/lib/mozilla/plugins/libmozjs.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libxpcom.so [/usr/lib/mozilla/plugins/libxpcom.so: wrong ELF class: ELFCLASS32]
Attempting to load the system libmoon
Segmentation fault


I assume is a bug in the Ubuntu tailoring of Firefox
csevcik is online now Report Post   	Edit/Delete Message

---

