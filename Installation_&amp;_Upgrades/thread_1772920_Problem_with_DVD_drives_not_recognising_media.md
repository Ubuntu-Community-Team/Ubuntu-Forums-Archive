---
title: "Problem with DVD drives not recognising media"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by shrdlu on 2011-06-01
This is a problem that started when I upgraded from 10.04 to 10.10 and is still there after an upgrade to 11.04. There was no problem when I was running 10.04.

I have two identical DVD writers attached to an IDE interface. (The hard disk is SATA.)

hdparm correctly identifies both DVD drives; sr0 and sr1.

/proc/sys/dev/crom/info shows both drives.

/etc/udev/rules.d/70-persistent-cd.rules seems fine

But neither drive recognises any media I put into it and if I try to mount them manually I get an error message saying sr0: unknown device.
:confused:

---

### Post by shrdlu on 2012-04-21
Problem resolved: a loose power-supply cable left the drives visible to the system but not fully functional.

---

