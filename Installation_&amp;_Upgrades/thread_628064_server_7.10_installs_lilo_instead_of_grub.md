---
title: "server 7.10 installs lilo instead of grub"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by NEtX on 2007-11-30
hi!

i installed ubuntu server 7.10 onto a logical volume called server. there is already a debian etch installed on it using grub to boot. but ubuntu forced me to install lilo into the mbr. actually i have no plan why it did so. i want to install xen and so i need grub to hide pci devices. did anyone have the same problem? why does it install lilo?

greeds,
NEtX

---

### Post by erlguta on 2008-04-17
I have the same question.
Why Ubuntu server install lilo instead grub?
In hardy server edition if you create LVM partitions it install lilo :confused:
It is not grub more advanced?

---

### Post by wkulecz on 2008-04-17
I don't know about grub being advanced or not, but it sure has been a lot more trouble for me than lilo ever was!

I'd say this is a feature not a bug!  I hope 8.04 offers me the option to choose lilo instead, I'd go back with zero hesitation!

Do a search on grub errors.  You'll see tons of posts and lots of "fixed it by re-install" or "I changed a lot of things and now it works, not sure why" but few actual fixes.  This is unacceptable on a server which you might need to get up fast after a hardware failure.

--wally.

---

### Post by erlguta on 2008-04-18
Yes. You are right.
Maybe grub is good to installations with another OS
but if you want one sever it is better one very tested loader.
Thank You.

---

