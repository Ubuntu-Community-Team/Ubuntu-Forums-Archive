---
title: "Question about wubi"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Lijnk on 2010-05-28
If I install a distro using Wubi, will the distro still be there after I uninstall Windows?

---

### Post by John Bean on 2010-05-28
No. The "disk" used is actually a file in the Windows file system, so removing Windows (and its filesystem) will also remove the wubi-installed system.

Edit: you could in theory remove Windows but leave the files used as disks, but I see absolutely no reason for wanting to do so - you may as well do a normal installation in the first place.

---

### Post by AcidMoon on 2010-05-28
Nope! If you remove Windows then the WUBI install will be removed too.
However you can remove the wubi install from Add/Remove programs and it won't affect your Window OS at all.

---

### Post by Lijnk on 2010-05-28
I'm having troubles with installing from a Live USB and was wondering if this was an option before I go out to get a pack of CD's. Thanks for the quick reply.

---

### Post by John Bean on 2010-05-28
You can convert a WUBI install to a "proper" one later, so it's a good option if you want to install without using a CD. After converting it to a normal installation you can of course remove Windows if you want.

See [http://wubi-installer.org/faq.php ]("http://wubi-installer.org/faq.php")

---

### Post by Lijnk on 2010-05-28
> **John Bean said:**
> You can convert a WUBI install to a "proper" one later, so it's a good option if you want to install without using a CD. After converting it to a normal installation you can of course remove Windows if you want.
 
See [http://wubi-installer.org/faq.php ]("http://wubi-installer.org/faq.php")
 
Thanks, I'll try this :).

---

