---
title: "rpm -i vs dpkg -i"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by marcantonio on 2006-02-18
Hey all,

Does dpkg have the ability to have multiple versions of the same package installed?

One thing I miss about rpm is when upgrading something like a kernel, where you'd want to keep the old kernel around for a bit to make sure the new one works, dpkg -i uninstalls the old version.  This is effectively what rpm -U does, which is fine in 99.9% of all cases.  But like I said, when doing a kernel I'd rather have something like rpm -i, which will keep both versions, and then remove the old version myself once I'm satisfied it's working.

Thanks,
Marc

---

### Post by cilynx on 2006-02-18
You can have two subversions of the same package installed.

It is perfectly legal and easy to have, say, 

linux-image-2.6.9-12 
as well as
linux-image-2.6.9-10 

Installed at the same time.  I don't see any reason to need two different versions of 2.6.9-12 installed at the same time.

The same thing scales up:

linux-image-2.6.9-12
as well as
linux-image-2.6.15-15

can be very easily installed at the same time...

Hope this helps...

---

### Post by Ocxic on 2006-02-19
yes it's possible and ussually won't cause problems the only time this won't work is dpkg specifically says it needs to remove a pervious version, which is rare if none existant.

---

