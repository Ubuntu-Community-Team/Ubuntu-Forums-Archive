---
title: "System won't log to encrypted /var"
date: 2015-12-31
forum: Installation &amp; Upgrades
---

### Post by os2 on 2015-12-31
I put the /var directory in a encrypted lvm.

The system isn't logging properly to /var/log.

I am guessing the volume is being mounted too late in the boot process as I am being asked for the passphrase quite late on and almost just before Xorg starts.

Is there a way to address this? Can I find out how to get the services reordered during boot so that the encrypted volumes are mounted earlier?

---

### Post by TheFu on 2016-01-02
Use whole drive encryption (dm-crypt) for everything except /boot. That is the only partition that doesn't need to be encrypted. It is easiest to set this up during the OS installation.  I've been unable to find a way to convert existing partitions that need to be decrypted at boot time.  Data partitions aren't important unless there are services which automatically start and look for the data.

---

