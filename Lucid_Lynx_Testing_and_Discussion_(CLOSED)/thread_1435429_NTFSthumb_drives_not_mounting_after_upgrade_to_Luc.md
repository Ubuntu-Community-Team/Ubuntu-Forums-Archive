---
title: "NTFS/thumb drives not mounting after upgrade to Lucid Alpha"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ken-san on 2010-03-21
Hi everyone. I just upgraded from Karmic x64, and, upon trying to access my NTFS disks/partitions (and upon further testing, also my USB drives), I get this from Nautilus:

Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.devicekit.disks.filesystem-mount-system-internal is not registered

Any clues as to why this is happening? And, more importantly, any way to fix it?
Thanks.

---

### Post by 666f6f on 2010-03-21
Hi,

I haven't installed Lucid yet, but it seems to me that the authorization dialog cannot be spawned (bug?).

Have you tried to mount NTFS partitions from the command line? (Here's how: [http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g))

Hope this helps

---

