---
title: "Error on Boot from Live USB (14.04.2 64 bit) - [3.074160] Unknown Controller Version"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by mcbobke on 2015-04-03
Hi everyone!

I'm trying to dual boot Win8/Ubuntu on my new Sager NP 9772-S laptop and am experiencing the following error when booting from a live USB:

"[3.074160] mmc0 Unknown Controller Version (3). You may experience problems."

After seeing this on an otherwise black screen, it just hangs here. A reboot did not resolve the issue, nor did booting into "try without installing" mode.

Does anyone have any ideas what might be causing this? I'm guessing it's hardware but Google results have been all over the place and many have not had the exact issue that I'm having.

Thanks!

---

### Post by dino99 on 2015-04-03
glance at post #28  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159)
also [http://www.linuxquestions.org/questions/linux-newbie-8/disabling-sd-reader-error-at-boot-mmc0-do-not-want-to-blacklist-875424/](http://www.linuxquestions.org/questions/linux-newbie-8/disabling-sd-reader-error-at-boot-mmc0-do-not-want-to-blacklist-875424/)

---

### Post by mcbobke on 2015-04-03
> **9d9 said:**
> glance at post #28  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159)
also [http://www.linuxquestions.org/questions/linux-newbie-8/disabling-sd-reader-error-at-boot-mmc0-do-not-want-to-blacklist-875424/](http://www.linuxquestions.org/questions/linux-newbie-8/disabling-sd-reader-error-at-boot-mmc0-do-not-want-to-blacklist-875424/)

I saw those links earlier and both seem to be under the assumption that Ubuntu has already been successfully installed. Am I incorrect in thinking that?

---

