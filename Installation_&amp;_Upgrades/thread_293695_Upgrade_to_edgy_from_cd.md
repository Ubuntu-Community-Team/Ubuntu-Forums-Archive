---
title: "Upgrade to edgy from cd"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by MblKiTA on 2006-11-05
How can I upgarde my kubuntu 6.04 to 6.10 using kubuntu-6.10-alternate-i386.iso?
When I run cdromupgrade from cd it gives the following: 

```

nikita@nik:/media/cdrom0$ sh cdromupgrade
Could not find the upgrade application archive, exiting

```

---

### Post by ReaderRat on 2006-11-05
I don't believe you can "upgrade" from a CD. What you need to do is re-install Kubuntu from the 6.10 Alternate CD.

---

### Post by ollienz on 2006-11-05
You can upgrade. Have a look at 'apt-cdrom-add'. I'm just looking into exactly how to do it, but basically you add the disc to apt as a source, then run the update manager and it uses the disc as the source for most of the upgrades.

---

### Post by ollienz on 2006-11-05
OK, ignore my previous comment. What you want is the command 

```
gksu "sh /cdrom/cdromupgrade" 
```

That should work according to the docs.

---

