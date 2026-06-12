---
title: "compileing kernel 2.6.35.2 on ubuntu 10.04"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by rvikinz on 2010-09-01
hi i m new user of ubuntu 
while installing a new kernel 2.6.35.2 on ubuntu 10.04 and on rebooting the system i got this

"-----------------------------"
Gave up waiting for root device. Common problems:
-Boot args (cat/proc/cmdline)
 -Check rootdelay=(did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/9181e083-9f0a-4892-b99f-770c97171637
does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
"-----------------------------------"

any help/suggestion would be appreciated

---

### Post by andrewthomas on 2010-09-01
what .config did you use?
I am assuming that your generic kernels will boot, but your custom one won't

---

### Post by dasgenie on 2010-09-01
lage rah vikas ........:popcorn:

---

