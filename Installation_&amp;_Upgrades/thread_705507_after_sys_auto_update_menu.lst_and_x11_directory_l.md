---
title: "after sys auto update: menu.lst and x11 directory lost (gutsy/7.10)"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by hanshansenhans on 2008-02-23
Hello!

Currently, i am using a dual boot setup with WinXP and Ubuntu Gutsy, Grub is the boot manager.
I did not boot Ubuntu for a while and after yesterdays startup, some auto system updates where done. A reboot was required.
After the restart, i realized that /boot/grub/menu.lst was altered - only ubuntu was in the OS list. Not a big problem, but additionally, the X-Server did not start as well, command line control was not possible either.
A start in recovery mode allowed to check on /boot/grub:
The menu.lst file had been changed. But the original file was not existing as menu.lst_bkp or something similar - it was gone.
In the /etc directory, X11 sub-directory completely vanished.

Any hints how to reverse this (especially, how to recover X11 dir)?

Thanks in advance,

Hans

---

### Post by taurus on 2008-02-23
Try reinstalling Gnome again with

```
apt-get update
apt-get install ubuntu-desktop gdm
shutdown -r now
```

---

### Post by hanshansenhans on 2008-02-23
Thanks, i am going to do so.
Is there any chance to find my old xorg.conf - it contained settings for dual display use...

Cheers, Hans

---

