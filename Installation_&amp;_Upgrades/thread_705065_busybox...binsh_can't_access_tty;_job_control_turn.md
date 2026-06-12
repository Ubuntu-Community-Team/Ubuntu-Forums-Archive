---
title: "busybox.../bin/sh: can't access tty; job control turned off"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by troutbum13 on 2008-02-23
I am trying to install from a live disc gutsy 7.10...this disc is known good I have done 2 recent installs with the same cd.
I am trying to install on an older abit AA8 mobo with 4 sata drives and 1 ide... I don't get very far in booting to the live cd when I get an busyBox prompt followed by 

/bin/sh: can't access tty; job control turned off
(initramfs)

I have searched and I found some older posts but nothing specific to gutsy...I tried adding irqpoll to the boot options...no joy.

Is this a known problem? I have tried using only the DVD drive and a single sata disk and it makes no difference...I disabled quiet in boot options and I don't see anything that jumps out at me although I don't know how I would know?? :lolflag:

If anyone can help or point me in the right direction I would appreciate it. thanks

---

### Post by confused57 on 2008-02-23
I don't have any experience with this problem, but this may help:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by troutbum13 on 2008-02-23
Thanks, I followed those instructions I get dumped to the initramfs prompt and modprobe piix returns a FATAL: module piix not found...most of that thread is about upgrading an existing install to fiesty...I will read all the way through and see if anything else may work.

---

