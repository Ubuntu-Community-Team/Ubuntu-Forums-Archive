---
title: "Use Propietary Driver from Live USB Environment"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by handsheldhigh on 2013-01-15
Hello, I'd like to test out the propietary driver for my Radeon 6290 on Ubuntu 12.10 in a live USB environment. How can I do this?

---

### Post by Mark Phelps on 2013-01-16
No simple answer -- as any of the usual solutions will require you to restart -- and once that is done, you are back to the original settings (default open-source driver).

Suggest, as a first step, you search for threads on making a persistant bootable USB.  There is a lot involved, and you need to get that working well before you trying installing restricted drivers.

---

### Post by efflandt on 2013-01-17
You cannot easily change kernel or video drivers on live/install iso, even with persistent data, because it initially boots from a fixed squashfs file system before persistent data is mounted.  Your choices are to remaster the iso with everything you want on it before writing it to USB, or do a regular install to a large enough USB device (8 GB minimum recommended).

---

