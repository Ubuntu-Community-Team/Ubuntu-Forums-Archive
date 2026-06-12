---
title: "XP / Ubunutu Dual Boot Problems"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by mr_simul on 2007-07-22
Hi all.

---

### Post by brownknight on 2007-07-22
Hi. What seems to be your problem with dual booth? You might want to check this thread below:

[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

---

### Post by mr_simul on 2007-07-22
Accidental Submit.  Sorry.

Anyway, my problem goes like this.  Dual boot seems to work.  Grub sees XP and Ubuntu, XP went on first, XP boots fine.  Live CD install of Ubuntu works, no prob.  Its when you try to boot ubuntu that it hangs, and then spits out:

udevd-event[1930]: run_program: '/sbin/modprobe' abnormal exit

Busy Box (blah blah)
sh: can't access tty; job control turned off
(initramfs)

and if I press alt+f1

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/70bfc441-54eb-4741-8137-0fad724877c4 does not exist. Dropping to a shell!

now, at the "initramfs" prompt, when I type "tty", I get "/dev/console", which one website told me was bad.  I've tried reinstalling ubuntu, and problem persists.  completely confused, and any help is greatly appreciated.  

thanks in advance.

---

### Post by Sir Funk on 2007-07-23
If you boot from the LiveCD could you try to find out the UUID of your drive that you installed to and then check it with that UUID?  I'm not sure of the command (maybe "blkid"?) but I've heard that some people get the wrong UUID and that's what causes this problem for some people.

-Funk

---

