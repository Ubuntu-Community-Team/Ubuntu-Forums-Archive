---
title: "Jaunty applesmc"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-02-23
Jaunty works great on my mbp 3.1 but I can't set the screen or keyboard brightness. That's applesmc's job correct... it's installed(upgraded from intrepid)  any body know of a fix?

---

### Post by cyberdork33 on 2009-02-23
> **hanzomon4 said:**
> Jaunty works great on my mbp 3.1 but I can't set the screen or keyboard brightness. That's applesmc's job correct... it's installed(upgraded from intrepid)  any body know of a fix?
There were various things that were changed I believe. As far as I know, all the changes to applesmc were added upstream and should be in the Jaunty kernel. Things like he changes to gnome-power-manager may not have made it though, I would check those in the PPA.

I don't know anyone using Jaunty (besides me) and everything works great on my iMac.

---

### Post by deltaiscain on 2009-02-24
Don't you also add mbp_nvidia_bl to the modules file(etc/modules)? Or is that only for penryn? And did you try installing the latest gnome power manager? I have mine from the Mactel PPA, version 2.24. [link]("https://launchpad.net/~mactel-support/+archive/ppa")

---

### Post by hanzomon4 on 2009-03-31
I fixed it

I'll post how later today

---

