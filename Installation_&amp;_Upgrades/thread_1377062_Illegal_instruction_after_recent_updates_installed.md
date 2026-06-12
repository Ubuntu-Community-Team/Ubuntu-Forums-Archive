---
title: "Illegal instruction after recent updates installed"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by grandrew on 2010-01-09
Hi all!

After recent updates install (9.10/x86) (update came something with libcrypt and kernels) almost every X/Gnome program now fails with 'Illegal instruction'. gdb(it can still function) says the signal is received in libgdk-x11-2.0.so.0 but I really doubt since gdk was not touched according to dpkg.log during the last update. I suspect that some of the new crypt libraries was compiled with specific CPU extensions and is now not compatible with my CPU (Athlon). Can I somehow reverse the update? Any other options? Maybe some thoughts how can I detect which exact module causes the exception maybe I could compile it by hand?

p.s. I didnt reboot since then and I fear to since it is likely I will not be able to boot into graphics mode anymore. Also it feels like filing a bug to launchpad since core libraries should not be compiled with specific proprietary CPU extensions or should use a compatible version at least for CPUs that do not support them.

---

