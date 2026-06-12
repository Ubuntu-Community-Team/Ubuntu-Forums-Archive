---
title: "Grub and root device missing (64bit system)"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by b3organ on 2011-08-20
Sorry if this has already discussed - couldn't find.
 
The problem after couple installations (10.10 --> 10.04 --> 10.10 --> 10.04-3) is that system goes to "busybox" after complaining about missing root device. I already have come to conclusion that this problem could be solved by telling the system that the root device is at sda1. However, I'm not able to start grub (by pressing "ESC") at boot before problems start. I'm able to start live-cd and I tried to install "over" the old one (same partitions without format, same username). No luck.
 
And in the busybox /proc/modules is empty for example. And the grub has worked with previous installations.

---

### Post by tom4everitt on 2011-08-20
This might help:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by b3organ on 2011-08-20
This is quite embarrassing because I noticed that last step of installation had "advanced" button. When I located the boot loader to hard disk which was first (in boot cycle) also according to bios everything started to work.

E: And the "how to restore grub from livecd" would have worked probably: [http://thpc.info/how/edit_grub_menu.html](http://thpc.info/how/edit_grub_menu.html)

---

### Post by tom4everitt on 2011-08-21
> **b3organ said:**
> This is quite embarrassing because I noticed that last step of installation had "advanced" button. When I located the boot loader to hard disk which was first (in boot cycle) also according to bios everything started to work.

E: And the "how to restore grub from livecd" would have worked probably: [http://thpc.info/how/edit_grub_menu.html](http://thpc.info/how/edit_grub_menu.html)

Okay, all good then :)

---

