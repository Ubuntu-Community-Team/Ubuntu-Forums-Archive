---
title: "firefox problems with intrepid upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by empty_tank on 2008-10-31
I recently upgraded to 8.10 (amd 64 version) and noticed that firefox was misbehaving - very slow in rendering pages.  No problems using Opera 9.61.  

I opened Firefox using CLI and it showed the following:

[INDENT]ICEDTEAPLUGIN_DEBUG = (null)
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
ICEDTEAPLUGIN_DEBUG = (null)
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message truncated
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
[/INDENT]


Can anyone help me decipher these error messages and how to solve the firefox problem.

thank you.

---

### Post by BenAshton24 on 2008-10-31
Try running this command, it will install Flash from adobe, (it appears that you already have this but just to be sure) and Extension libraries for flash which provides the libflashplayer.so plugin, this should fix it :D
> sudo apt-get install flashplugin-nonfree flashplugin-nonfree-extrasound

Hope this helps :D

--Ben

---

