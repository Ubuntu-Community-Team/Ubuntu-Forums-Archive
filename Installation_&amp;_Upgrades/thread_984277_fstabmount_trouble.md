---
title: "fstab/mount trouble"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by petrim on 2008-11-16
Well, I'm apparently stuck.

I need to install a disk as /opt, so I threw it in and defined it in fstab as:
/dev/hdb1 /opt ext3 defaults 0 2

Turns out everything on the disk is in a folder called opt - or so I'm guessing, since the contents were at /opt/opt after booting.

So I unmounted the volume and re-mounted it a folder up (to root)... well, it seemed logical at the time.

But unsurprisingly there's a folder called /opt on the root drive already and so the hdb1's content wont show at all.

And now I can't unmount it, apparently 'cause it's root.
root@kayak:/# umount /dev/hdb1
umount: /: device is busy
umount: /: device is busy

The error appears twice, which points to umount trying to unmount the 'real' root as well.

How do I fix this? I'm guessing I need to fix fstab and boot, but please do advice. Can I just remove the /opt I see now to fic this, it looks empty...

---

### Post by taurus on 2008-11-16
Make sure you are not in the mountpoint of /dev/hdb1 before you unmount it or you would get that error message.  Where did you mount /dev/hdb1 to anyway?

Is it a clean disk or does it have some files on it, /dev/hdb1?

---

