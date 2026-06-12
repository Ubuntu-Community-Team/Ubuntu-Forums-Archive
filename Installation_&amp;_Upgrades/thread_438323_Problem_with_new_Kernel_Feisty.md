---
title: "Problem with new Kernel Feisty"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by nestor2509 on 2007-05-09
Hi I have a problem when I try to start with Ubuntu new kernel 20.15 is that it doesn't load at all.
When I click Alt+F1 that appear:
*mdadm: No devices listed in conf file were found*
Any ideas of how I can resolve this? I really appreciate it.
Thanks

PD: Sorry about my poor English

---

### Post by nestor2509 on 2007-05-09
Please if someone could help me. I don't know what to do...
Thanks

---

### Post by er0k on 2007-05-12
This happened to me when I tried to disable gdm.

I booted into recovery mode from the grub menu (hit esc at the menu) and ran ```
update-rc.d gdm defaults
``` from the root prompt and it works again.

Maybe you could also try booting from an older kernel in the grub menu.

---

