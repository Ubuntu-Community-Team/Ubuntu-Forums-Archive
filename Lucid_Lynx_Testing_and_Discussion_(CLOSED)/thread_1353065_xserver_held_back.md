---
title: "xserver held back?"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-12-12
My lucid install, upgraded from karmic, has 13 xserver-xorg packages held back. The reason appears to be a confused conflict between the xx-input-all and xx-video-??? packages. I don't have xx-video-all installed, just the minimal set for my ATI graphics. If I try to install xx-video-all synaptic offers to remove most of the xx-input- packages.   Are these being replaced by something else, or am I right to be reluctant?

Anyone else having this? I have seen a few comments in other threads about upgrading xorg, but nothing to suggest problems.

---

### Post by Tompalaz on 2009-12-12
I upgraded those packages. @ restart I was dropped to cli. Managed to fix it but now the sensors in my macbook acts like a joystick, (see the 'new X-server, new joystick' thread.)

---

### Post by ranch hand on 2009-12-12
My desktop does fine with them.

---

### Post by scradock on 2009-12-12
> **ranch hand said:**
> My desktop does fine with them.
But did you accept the upgrade that removes xx-input-?? packages? I have a Synaptics touchpad, so I'm wary if the update says it will remove xx-input-synaptics, for instance......

---

### Post by scradock on 2009-12-12
Finally managed to break the log-jam without breaking the display - removed a couple of the -input-?? packages [?? = vmmouse, mouse, if I remember correctly] then went for an upgrade on the remaining xserver-xorg packages. It brought in all the -video-?? drivers again, but they then removed cleanly (apart from the ones I need, of course). The curious part is that the -input-kbd package has gone - must be handled some other way, I suppose...

The -input-mouse and -input-vmmouse packages did come back, incidentally, and the -input-synaptic package is still there.

---

