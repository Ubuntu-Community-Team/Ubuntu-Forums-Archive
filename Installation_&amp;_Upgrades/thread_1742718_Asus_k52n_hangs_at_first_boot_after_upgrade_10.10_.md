---
title: "Asus k52n hangs at first boot after upgrade 10.10 - 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by milovanderlinden on 2011-04-29
Hi folks,

I wanted to share the solution I took to fix my Asus k52n laptop now running 11.04 64!

Last night I decided to take on the challenge and upgrade my distribution from 10.10 to 11.04. It took a while to run, but when I booted this morning, no luck. I managed to go into tty by pressing ALT+F1 and the /var/log/xserver.0.log showed me that xserver failed to start. It ended up with a segfault.

The solution:

1. Boot into recovery (with my grub, the second line)
2. Boot into failsafe
3. Select failsafe graphical mode
4. Make sure you have a network
5. Go to additional drivers
6. Activate the ATI proprietary driver
7. Wait a while
8. Reboot

Now the segfault is gone and my system is running flawless with unity and all.

Thanks Canonical and team for making this wonderful new distribution available!

---

