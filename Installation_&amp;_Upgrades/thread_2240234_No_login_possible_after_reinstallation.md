---
title: "No login possible after reinstallation"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by JulienDe on 2014-08-18
My computer was running with a former LTS, and had 3 partitions: /, /home and swap; the /home partition was encrypted. I switched to the new LTS (10.04) on the same computer, hence with the same partitions. The installation was not without trouble - I had to use Boot-repair to get the computer to relaunch after the new install. But once it agreed to boot, now when I come to the login page, it recognizes my password (it does not tell me that it is wrong, which it does when I enter a wrong one), but gives me nothing but yet again the login page, over and over.
Thanks for your thoughts!

---

### Post by JulienDe on 2014-08-20
The solution was simple: the problem was just that during the install I had chosen a new password, different from the password I had used so far, so my files could not get decrypted. Stupid me...

---

