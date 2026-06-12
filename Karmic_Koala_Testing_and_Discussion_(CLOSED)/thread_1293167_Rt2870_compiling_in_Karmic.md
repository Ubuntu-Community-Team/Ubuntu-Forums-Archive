---
title: "Rt2870 compiling in Karmic"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thecow on 2009-10-16
Has anyone gotten the RT2870 driver from Ralink to compile in Karmic?  It gives me various compiling errors which didnt used to happen in Jaunty.  Is this something with the new kernel?  Or is it  something else entirely.  Just wondering if anyone else has tried this

---

### Post by RaZoR1394 on 2009-10-25
It must be something with the new kernel as I'm having the same problem on a Debian PPC system with the 2.6.31 kernel.

---

### Post by dude2425 on 2009-10-25
You would have to patch it to convert to the netdev_ops api. I had the same trouble with the RT2860 in my EeePC 1000H.

You may be able to find a patch with Google already made for the version you're compiling.

---

