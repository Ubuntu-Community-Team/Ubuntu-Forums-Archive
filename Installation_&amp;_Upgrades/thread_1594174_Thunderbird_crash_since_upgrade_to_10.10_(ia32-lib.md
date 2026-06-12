---
title: "Thunderbird crash since upgrade to 10.10 (ia32-libs pblm ?)"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by jolig on 2010-10-12
Hi,

I've upgraded my 10.04 (64bits) into 10.10 (64bits) on sunday and since I can't get thunderbird working anymore, I get the following error :

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nppdf.so [/usr/lib/mozilla/plugins/nppdf.so: wrong ELF class: ELFCLASS32]
Inconsistency detected by ld.so: dl-open.c: 612: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

It seems nspluginwrapper has similar issues...

I've seens there has been similar problems with skype but downgrading to ia32-libs_2.7ubuntu26_amd64.deb didn't fix the problem.

Any idea ?

Cheers

---

### Post by jolig on 2010-10-12
Sorted out !

I seems to be related to the nvidia drivers that were still installed on my computer while i now have a ATI driver (don't understand the connection, but everything is working fine now including flash, thunderbird & chrominium...)

Hope this will help someone !

---

