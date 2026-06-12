---
title: "usb filesystems need authorization to mount and then mount read-only"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2009-06-11
Recently when plugging in my card reader or my mp3 player I need to authorize the mount, after doing it mounts the device, but read-only, anyone else experiencing this?

---

### Post by inportb on 2009-06-11
I think it's read-only because the owner is root; at least, that's what you get if you mount as root. I don't know why it requires root, though.

---

### Post by Benjamin_Lebsanft on 2009-06-11
might be related to the missing groups bug, I don't know for sure though

---

