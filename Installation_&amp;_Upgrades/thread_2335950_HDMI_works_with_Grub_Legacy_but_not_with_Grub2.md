---
title: "HDMI works with Grub Legacy but not with Grub2"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by Nibblyn on 2016-09-02
It seems that Grub2 prevents the HDMI output to activate even though it is reported and handled by the system as if it was working properly.

More verbose description here: [https://ubuntuforums.org/showthread.php?t=2334805](https://ubuntuforums.org/showthread.php?t=2334805)

Is there some module to blacklist in Grub2 or some kernel boot parameter to add in order to use Grub2? Should this be considered a bug in Grub2? Thanks.

---

### Post by Luke M on 2016-09-03
Have you tried 

GRUB_GFXMODE=text

in /etc/default/grub?

---

### Post by Nibblyn on 2016-09-20
Thanks Luke M for the answer!

I believe I've tested every possible Grub2 configuration and none of them works while Grub Legacy simply does out of the box. It also solves the problem of the second operating system (Windows) which randomly (about 50% of the time) crashes during startup. I believe that the problem can be considered solved as a kind of non-compatibility of Grub2 related to the hardware.

---

