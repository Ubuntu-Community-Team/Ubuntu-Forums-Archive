---
title: "GRUB Entry For A Second Hard Drive"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by Virtute on 2006-10-09
So heres the deal - I have 2 40 gig hard drives.  The first (/dev/hda) has Win2k on it, and the second (/dev/hdb) has Ubuntu on it.  GRUB is having issues, though, so I'm gonna need to make a custom entry for the second hard drive and possibly the first.  Can someone tell me how to do this?

---

### Post by az on 2006-10-09
> **Virtute said:**
> So heres the deal - I have 2 40 gig hard drives.  The first (/dev/hda) has Win2k on it, and the second (/dev/hdb) has Ubuntu on it.  GRUB is having issues, though, so I'm gonna need to make a custom entry for the second hard drive and possibly the first.  Can someone tell me how to do this?

It would be helpful to know the specific problems you are having.

---

### Post by Virtute on 2006-10-09
On boot, GRUB fails to show any sort of loader.  Simply says "GRUB" with no prompt at all and nowhere to go.

---

### Post by az on 2006-10-09
> **Virtute said:**
> On boot, GRUB fails to show any sort of loader.  Simply says "GRUB" with no prompt at all and nowhere to go.

Does it freeze?  Are you able to enter in the option at the grub editor and then boot that ?

What kind of copmuter is it (very old or very new?)

---

### Post by gn2 on 2006-10-11
Here's an alternative strategy for dual-booting:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

You would need to "fixmbr" from recovery mode on the Windows CD.
.

---

