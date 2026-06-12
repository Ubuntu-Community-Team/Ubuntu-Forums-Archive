---
title: "Fatal error with FUSE"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Simplicius on 2009-10-13
Hi,

I'm using Karmic and am very happy with it. I'm trying to install encfs (here is the howto: [https://help.ubuntu.com/community/FolderEncryption]("https://help.ubuntu.com/community/FolderEncryption")) and when I do this:

> $ sudo modprobe fuse

I get

> FATAL: Module fuse not found.

Any idea?

---

### Post by medeshago on 2009-10-13
I'm having the same problem.

---

### Post by Seq on 2009-10-13
Fuse appears to be built-in now, so it is no longer a removable module.

---

