---
title: "remote desktop disabled after 20.04 to 22.04 upgrade."
date: 2022-09-10
forum: Installation &amp; Upgrades
---

### Post by DraconPern on 2022-09-10
Just did an upgrade from 20.04 to 22.04 and the remote desktop option was disabled afterwards.  This setting should carry over.

---

### Post by TheFu on 2022-09-11
Which DE?

I don't have 22.04, but I understand the Gnome4 Remote Desktop is Wayland-only and works best between 22.04 systems.


If you want to free yourself from that, check out x2go.  It only works with Xorg X/Windows, not Wayland, but it has improved security as provided by the NX protocol and is 2-3x faster than RDP or VNC options.  There are x2go clients for Windows, OSX, and Linux.  The server is Linux-only, I believe.   Also, x2go doesn't work with either Gnome3+ or KDE DEs, so you'll need to pick any of the lighter DEs - XFCE, Mate, LXQt, Cinnamon, .... or a pure WM-only setup.  Setting up x2go always begins by setting up an ssh connection between the system, since ssh is the authentication method used for NX protocols.

If you are unwilling to use x2go, just ignore me and I'll end my subscription to this thread in a day or so.

---

