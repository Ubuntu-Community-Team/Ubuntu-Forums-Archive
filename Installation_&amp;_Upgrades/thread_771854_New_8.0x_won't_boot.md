---
title: "New 8.0x won't boot"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by trent_shipley on 2008-04-28
I upgraded to Ubuntu 8.03.  Now, during the post-boot initialization process the system goes into a fugue trying to  mount something, probably the CD/DVD drive.

It keeps trying:

ata2.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 Action Frozen
ata2.00: cmd a0/00:00:00:24:00/ et cetera
ata2.00: status {DRDY}

So I try to use the CD of Ubuntu 7.10 that came with the Dell system as a rescue disk.  (Dell does not seem to have re-branded the DVD.)  It won't work as a rescue disk.  So I mount the hard drive at /hdroot and copy /hdroot/home/ to an external hard drive over fire wire.

I wipe the disk and reinstall 7.10.  It boots.  I try to upgrade to 8.04.  Maybe whatever is wrong will be fixed.  No luck.  I get the same error.

Someone in the local Phoenix LUG has suggested this is a chipset issue.  If that is so, why would the old version work and not the new version?

---

