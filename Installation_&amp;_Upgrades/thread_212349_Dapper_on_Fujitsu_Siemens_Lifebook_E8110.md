---
title: "Dapper on Fujitsu Siemens Lifebook E8110"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by robban on 2006-07-09
Has anyone been able to succesessfully install Dapper on this laptop? I have tried every possible way, but no luck. Breezy does install, but lacks many of the drivers.
Opensuse 10.1 does install and works correctly!

This bug is created on Launchpad!
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/48510]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/48510")

---

### Post by gregik on 2006-08-01
I have same machine and same problem.

Hmm! 
3 weeks and no progress or am I missing something?

---

### Post by ambrish on 2006-09-22
Same with me. Cannot install through live. Installation just hangs.
Installed with alternate, always hangs while installing. The last thing i saw was while it was installing xserver.
HEELLPPP !!

---

### Post by carontis on 2006-09-22
Some kind of laptops are prepared with MSWindows and there are also hidden partitions called _system_save. You should try to delete all the entire hdd with a low level format (you can use Autoclave; it makes a simple fd with a particular low-level based boot). After that, your hdd will be as a new one and you will not need to jump in BIOS for the chance of boot, or starting with F12 / F11 pressed, but it will do all by itself.

---

