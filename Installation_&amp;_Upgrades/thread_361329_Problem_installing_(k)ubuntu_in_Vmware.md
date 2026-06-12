---
title: "Problem installing (k)ubuntu in Vmware"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by hugoboss on 2007-02-14
I all,

I'm running XP and I want to install ubuntu 6.10 in VMware for now (I'll install dual boot after).
I created to partitions: 7,5 Gb formated in ext3 and 512 Mb linux-swap. The installation goes fine until grub installation.
It gives a fatal error and the instalation is stopped.
My question is: where sould I install grub? By default, the instalation is in hd0, but my "disc" is /dev/sda.
Thanks in advance,

Hugo Boss

---

### Post by hugoboss on 2007-02-14
After trying another time to install it, the messge in /var/log/syslog is grub-installer [....] exited with error code 1.
Any help?

---

### Post by hugoboss on 2007-02-15
I now know what the problem was: I manually edited the partition table and created partitions like in a real machine.
So, the solution is doing nothing (simple press the next button) in step 5.

---

