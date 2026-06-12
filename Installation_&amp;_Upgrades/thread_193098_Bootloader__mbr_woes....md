---
title: "Bootloader / mbr woes..."
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by pyromidget on 2006-06-09
Hey all - I'm trying to install dapper onto my main box, but the installer always seems to go tits-up at the bootloader stage...

When I originally got the box it had Win2k on it, but despite the fact that Windows was completely wiped off of it months ago, AND the drives (3 in a raid5 setup) have all been through about a gazillion formats PLUS the fact that I've deliberately overwritten the MBR on each drive with:

```
dd if=/dev/zero of=/dev/sd(a/b/c etc) bs=512 count=1
```
The installer STILL detects Win2k on the computer when installing GRUB.

If that weren't enough, once the cd has ejected and the box restarts it just stalls after 'Verifying DMI pool data...' (usually GRUB pops up right after this).

I'm convinced that both problems are related, so can anyone suggest a way of TOTALLY wiping the drives clean as if they were brand new?

---

### Post by pyromidget on 2006-06-10
Anyone got any ideas?  If i need to post up more info then just ask and i will, but i'm pretty new to linux so you will have to tell me!

I really don't want to go back to Windows but if nobody can help then i'm not gonna shell out a couple of hundred quid for new hard drives... :(

---

