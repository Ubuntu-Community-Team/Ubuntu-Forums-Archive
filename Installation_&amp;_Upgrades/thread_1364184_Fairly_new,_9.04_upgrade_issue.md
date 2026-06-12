---
title: "Fairly new, 9.04 upgrade issue"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Redinger.Chris on 2009-12-25
Word of warning, I'm fairly new to Ubuntu, still rather unfamiliar with it, but I've made progress.

So I run 9.04 on an Acer d250, dual-booted with XP. Installation went well, it's ran great for the last 3-4 months. I tried to do a java download via firefox, and it wouldn't finish, and said I had a broken package. So, following the prompts, I started Synaptic, used the 'broken' filter, and then hit 'fix broken' and it was fine. I was bored, so I went in and used the 'upgradable' filter, and downloaded 205 megs of stuff to upgrade. Went fine, needed system restart, did it, and this happened:

Loading, please wait...
udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
 -Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/43a26aa4-d35e-44c7-8552-d115f58ff1ce does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help for a list of built-in commands.

(initramfs)


typing help gives a list of commands that I have no idea what to do with. So... if someone knows what to do would give me directions to my goal of making it run right, I'd be able to do it next time as well. So... what do I do?

---

### Post by Redinger.Chris on 2009-12-26
UPDATE: I have 9.10 UNR running on a third partition, installed it to try it out, but rarely used it. I'm using that installation to recover all my files off 9.04, and will be reinstalling it on the same partition. It's the only option I have at the moment, unless someone has any ideas. Cheers!

CR

---

