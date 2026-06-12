---
title: "upgrade 10.04 and no keyboard on VostroV13"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by jkfeldt on 2010-05-14
I recently upgraded my Dell Vostro V13 from 9.04 to 10.04. All seemed to go well,
but now the keyboard (and touchpad) aren't being recognized on bootup.

I can get to single user mode OK --- keyboard is fine, but something is badly amiss as
I can't use the mouse or keyboard when the X-server starts.

Help!

---

### Post by jkfeldt on 2010-05-15
I 'fixed' this issue when I realized that Grub was not displaying the newly upgraded OS (vmlinuz-2.6.32-22), and was trying to boot the old OS (2.6.28-11) which would not properly load.

This may have something to do with the fact that I am running Kubuntu....dunno.

I still don't know why Grub isn't properly displaying the new OS, and editing the OS
options on booting is a problem.

Any idea of how to get Grub 2 to display the right OS?

---

