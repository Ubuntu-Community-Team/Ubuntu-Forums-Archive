---
title: "AOne and Karmic upgrade: &quot;fsck./ not found&quot;, mounting problems"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2009-12-17
Having some annoyances here with my otherwise nicely working Asus Aspire One which I recently upgraded to Karmic... every now and then, at boot, I get the following:

```

fsck from util-linux-ng	2.16
fsck: fsck./: not found
fsck: Error 2 while executing fsck./ for /dev/sda1
mount: mount point UUID=... does not exist
mountall: mount UUID=... [396] terminated with status 32
mountall: Filesystem could not be mounted: UUID=...

```

The UUID hashes are correct, just didn't type them out here as I had to copy this manually from tty :)

It seems like the regular fsck fails, apparently because of a typo in some script... no wonder it can't find "fsck./". The funny thing is that after some messing about and repeating the mount-mountall complaints ~10 times, it manages to mount root just fine, and the drive and filesystem are ok.

So I guess the first question is... from which script is fsck run from?

---

