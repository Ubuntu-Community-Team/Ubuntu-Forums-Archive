---
title: "update one package only (cdrom automounter)"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2010-07-25
Hi
can I update only one package? CDrom automounter is broken in 10.04 and very annoying. So hopefully this can be fixed....
Thanks
Michael

---

### Post by efflandt on 2010-07-25
Maybe there is something I do not know about.  But the only issue I had with auto mounting CD/DVD or USB drives in 10.04 was due to Linux errors trying to read a phantom floppy (due to a hot swap drive bay) that did not exist on an old Dell Inspiron 8200 laptop.  In that case I had to **blacklist floppy** (in a file in /etc/modprobe.d) and I think **sudo initramfs -u** so it did not try to load floppy module during boot.  Some people had success just disabling their floppy in BIOS (CMOS set up), but that did not seem to work for the hot swap bay.

---

### Post by ahso4271 on 2010-07-26
To complicated. Is there no fix to my cdrom of 10.04? Cannot believe such.....lot of people seem to have issues. Yes after installation 10.04 tried to mount floppy which i don't have anymore on my pc but a cdrom.
changed in /etc/fstab floppy to cdrom but still cannot burn with k3b as it's not recognised.

---

