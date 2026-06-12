---
title: "RadeonHD: &quot;software rasterizing&quot; and low FPS unless root"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by quazar on 2009-12-16
I've installed kernel 2.6.32 on Ubuntu 9.10 in order to use the RadeonHD drivers for my HD3200 IGP.
I'm now running Ubuntu with RadeonHD drivers, but I only get
decent 3D support and hardware rasterization when running as root:
```
glxinfo | grep "renderer string"
```
it returns: "software rasterizing" unless I run the command as root.
Also, glxgears runs 5x faster as root...

What do I need to do to get full 3D support as a normal user?

---

### Post by quazar on 2009-12-17
Great, a reboot solved the issue!
Now I can finally enjoy tear-free video!

edit: this appears to be a known issue:

from X.org Wiki:
11.4. I only get a very jittery display
You probably used the fglrx driver before. It doesn't restore the linebuffer completely on exit. You have to reboot your system to get this fixed. In some rare cases you might even have to power it off and restart it. Suspend to disk & resume is reported to work on many systems as well.

---

