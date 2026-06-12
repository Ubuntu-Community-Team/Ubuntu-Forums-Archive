---
title: "Running ZFS raidz2 on XUbuntu 12.10"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by VanderveckenSmith on 2013-03-13
Hi,
I'm having serious problems running a ZFS filesystem in an external enclosure running raidz2.  I've had it up and down for weeks, and it regularly exhibits the kind of problem I'm seeing now.
My XUbuntu system is fully updated, and I'm running the Ubuntu native zfs package.  I've also got grub running the drives with libata.force=1.5G and libata.force=noncq.
As soon as I mount the filesystem the drives go haywire.  I've attached the dmesg in a zip file (because it's so large).  It's in 3 parts.
Part 1 is the base server startup.  Part 2 is what happens after I turn on the external enclosure and let everything come to equilibrium.  Part 3 is just after I run
[code]sudo zfs mount storage[code]
That's where all the crazy behaviour is.

Anyone know what's going on?

Thanks,
Vandervecken

---

### Post by VanderveckenSmith on 2013-04-06
It turned out to be a faulty Port Multiplier (hardware piece in the external enclosure)

---

