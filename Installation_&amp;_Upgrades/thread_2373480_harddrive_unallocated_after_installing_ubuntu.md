---
title: "harddrive unallocated after installing ubuntu"
date: 2017-10-06
forum: Installation &amp; Upgrades
---

### Post by imdoneok on 2017-10-06
i just tried to install ubuntu and after that my hard drive isn't listed in bios boot options and it shows unallocated in boot-repair and sad thing is recommanded boot repair bottom isn't available
here is the log:[http://paste.ubuntu.com/25686424/](http://paste.ubuntu.com/25686424/)

---

### Post by dino99 on 2017-10-06
of course, the first issue you need to fix is the bios one: check how that disk is plugged, their jumpers in case of. You probably have some indications on the hardware itself, or a doc about it.
Then you need to partition it, and finally install ubuntu on it.
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

In case you are talking about the grub menu, and already have some other OSs installed, then you need to run 'sudo update-grub' from a working linux install.

---

