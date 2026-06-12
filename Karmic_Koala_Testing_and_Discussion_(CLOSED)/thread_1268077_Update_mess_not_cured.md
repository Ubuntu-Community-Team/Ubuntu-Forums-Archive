---
title: "Update mess not cured"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-09-16
So, I don't know if there's help for me, but after doing the upgrade and dist-upgrade after the big upstart fiasco, I am still having problems.

After Grub, I get a few udev errors that I can't really remember right now (one said something about my kernel name), the "no resume image found, doing normal boot," some more udev errors, and something that says my BIOS is unrecognized (Gateway CX2619). Then my screen goes black like before. There is still stuff going on- I can type commands and such and the hard drive light flashes.

Not sure what's going on, as everyone else seems to have fixed the issue... I'm thinking I'm going to have to wait until Alpha 6 and do a fresh installation.

Also, I can't get to the recovery console. It does the same behavior.

---

### Post by dino99 on 2009-09-16
ok, lot of people have problems. last upgrades of libc, udev, dbus have broken configs.

Like yours, mine is down & i only upgrade with chroot from jaunty 32.
Curiously problems happens now like with Hardy, not with previous alpha.
I think we need a few days for debugging.

---

