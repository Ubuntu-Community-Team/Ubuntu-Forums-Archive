---
title: "Monitor &quot;out of range&quot; after installing Ubuntu 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by hongquan1987 on 2011-10-14
Hi all,

After installing Ubuntu 11.10 (Ocelot), my PC failed to start with the "Out Of Range" error in the monitor, then stop.

The LiveCD can show the "Install" program, but if run as "Try Ubuntu", only the wallpaper and the cursor were shown, all other elements of desktop were fuzzy and unresponsive. I cannot launch any app apart from "Ctrl + Alt + F1".

I think the problem is at the VGA driver. My computer use onboard GeForce 6100 VGA, which works with Ubuntu 11.04 and older.

How can I downgrade the graphic driver inside the LiveCD, then re-install it onto the harddisk?

The LiveCD can be booted with nomodeset to display full desktop (though ugly).

==== Update

Maybe the problem is the kernel. How can I downgrade the kernel?

---

### Post by hongquan1987 on 2011-10-14
I tried again, pressing some arbitrary keys then the boot screen showed up (don't know why the "Out of Range" disappeared). After waiting a while for checking disk, I logged on successfully, installed nVidia driver, changed the resolution setting in GRUB and now my computer can boot normally.

This topic now can be closed.

---

