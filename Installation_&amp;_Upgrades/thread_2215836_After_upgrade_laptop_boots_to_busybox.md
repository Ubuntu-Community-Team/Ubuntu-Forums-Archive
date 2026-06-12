---
title: "After upgrade laptop boots to busybox"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by Snotnose on 2014-04-08
Did a command-line update from 12.04 to 13 something.  When it was done it said I needed to reboot to finish, so I let it do a shutdown.  The system froze.  I let it sit there for an hour, then just turned it off.  Now when I boot into Ubuntu it boots into busybox.

How can I fix this?  I'd prefer to not lose my /home directory, but no biggie if I do.

---

### Post by Double.J on 2014-04-08
Hi there! 

Welcome to the forums, sorry to hear about your situation.

do you get any error messages at boot like 'couldn't find...'?

the two most common causes of ending up at busy box are grub looking on the wrong place or the system not being able to mount an fs it needs.

from a livedvd/usb, try running b[oot repair]("https://help.ubuntu.com/community/Boot-Repair"), also check your install's /etc/fstab file to check everything is correctly listed.

there's no need to worry about /home - worst case you can copy if using a Live cd.

 All the best, keep us updated!

Jj

---

