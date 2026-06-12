---
title: "Ubuntu wont boot right after upgrade."
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by Kyomaru on 2011-11-02
The other day, I upgraded my laptop, which is running 10.10. It upgraded linux headers to 2.6.30. i restarted, and it wont boot. it will boot fine if i chose the ubuntu with the older linux headers in Grub, but it wont boot with the new ones. If i cant fix it, just being able to change its position in grub would be great. Since its on the same hard drive though, i dont think id be able to accomplish that. could someone help me out.:confused:

---

### Post by rng on 2011-11-02
Try opening (as root) /boot/grub/grub.cfg and see which menuentry you want higher up in menu.

---

### Post by Kyomaru on 2011-11-02
Thank you so much. it worked. YAY! :D

---

