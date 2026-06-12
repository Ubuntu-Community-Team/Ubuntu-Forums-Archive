---
title: "Mounting external usb drives"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by justanotherhandle on 2011-01-09
Reinstalling/updating to Lucid and I had moved the old home directory to an external usb hard drive.

Trying to move back is a problem as when I plug in the usb drive I'm getting this error:

```
Not Authorized: Remote Exception invoking 
org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on 
/org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: 
org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file 
not found or permissions invalid
```

The drive has two partitions, a 50 gb Fat32 and a 200 GB ext3 (or ext4 ... not sure I remember which) partition.

I was also unable to mount a usb flash drive also formated with Fat32 with the same error.

Help!

---

