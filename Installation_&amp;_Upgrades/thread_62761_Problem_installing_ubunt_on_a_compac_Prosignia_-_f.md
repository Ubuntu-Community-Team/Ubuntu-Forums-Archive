---
title: "Problem installing ubunt on a compac Prosignia - framebuffer, I supose..."
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by ispmarin on 2005-09-05
Hello all!

Here it comes: I am trying to install ubuntu hoary on a very old compac prosignia laptop (PII, 233MHz, 10 Gb...). The installation fails when I try it directly - I had to put debian-installer/framebuffer=off to work out this problem. Ok, then, but when the system reboots, I think that base-config uses framebuffer too, and I got a black screen. So, what can I do to a)disable completely the framebuffer at boot time, b) put it to work, or c) make the base-config works correctly and my monitor too?

Thank you!

Ivan

---

### Post by ispmarin on 2005-09-09
Hello all!
I finally solved this problem: the problem was that base-config uses framebuffer, and was being executed after the first reboot because a line in /etc/inittab. I removed the line and installed all the packages by hand. Worked!

Now just have to install the sound card and the modem... uff!

bye!

Ivan

---

