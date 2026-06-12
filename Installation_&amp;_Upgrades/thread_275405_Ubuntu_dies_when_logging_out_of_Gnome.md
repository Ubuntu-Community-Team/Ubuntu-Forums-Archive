---
title: "Ubuntu dies when logging out of Gnome"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2006-10-11
Hi,

I have got an annoying problem with Ubuntu whereby it will completely die when I log out of Gnome.

The screen becomes garbage and the whole PC is locked up, the only way to remedy this is to soft-reboot.

I have had this issue with Ubuntu in the past and was hoping it had been fixed. I tried doing another fresh install without any nVidia GLX drivers installed and still had the same issue.

Currently the system is as follows:

Ubuntu 6.06
Kernel 2.6.15-27-686
nvidia-glx modules installed (from the default apt source list)
nVidia GLX with RenderAccel enabled
Dual Screen configuration @ 1600x1200x85hz resolution

Hardware:

Dual P4 Xeon with Asus PC-DL motherboard
2gb DDR-333 Ram
PATA Hardrives and Raid config
nVidia 5950 Ultra AGP 256MB graphics card
2 x Eizo F930 screens.

I have no problems using another distro (also run Debian 3.1 with Xfree86 in a similar dual screen config), seems only to affect Ubuntu.

Thanks in advance,

Fz

---

### Post by luckyjunknowitz on 2006-10-11
finalzero,

I had the same thing happen to me a few times.  After looking at the log I found that it was hanging because of something related to the "splash" screen.  If you change your boot options in grub to NOT use splash, then it should work fine.  You'll also get a whole stream of messages that describe what's happening during boot and shutdown/logout.

If you remove the keyword 'splash' from your grub boot command, then it should work fine.

If you're not familiar with GRUB, and the startup commands or how to edit and change them, check this link out: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Let me know if this fixes the problem.

BTW:  This is a temporary fix though since if the problem is in the splash screen stuff you're only eliminating the cause, not fixing it.

Cheers,

Luckyjunknowitz

---

### Post by finalzero on 2006-10-11
I had a feeling it was something to do with that as it seems the framebuffer was full of garbage from the boot splash screen.

To be honest I am not a fan of splash screens, I prefer to see what is actually happening during boot and it saves me having to dive into the syslog file each time.

I only came across the framebuffer when I was installing XGL and Compiz, during the config I was messing about with some plugins and noticed partial artifects from the boot screen were present.

I'll give your suggestion a go.  Also read something about Unsplash, is that related or for a different part of ubuntu altogether?

Thanks in advance,

Fz

---

