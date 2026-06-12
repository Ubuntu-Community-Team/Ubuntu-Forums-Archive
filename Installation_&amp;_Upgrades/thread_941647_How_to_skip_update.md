---
title: "How to skip update?"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by jmjohn on 2008-10-08
Hey all,

I've got this error when updating libpigment.so (no clue what that does)

E: /var/cache/apt/archives/libpigment0.3-7_0.3.10-1~ppa1_i386.deb: trying to overwrite `/usr/lib/libpigment-0.3.so.8.0.0', which is also in package libpigment0.3-8

First, can anyone tell me what this error means, second, can anyone tell me how to skip an update permanently?

Thanks,
glass.dimly

---

### Post by 73ckn797 on 2008-10-08
> **jmjohn said:**
> can anyone tell me how to skip an update permanently?

Thanks,
glass.dimly


Go to System/Administration/Software Sources/Update.
Turn off updates by unticking each option.

---

### Post by Partyboi2 on 2008-10-08
If you are not wanting to update a particular package you can lock the package version in synaptic package manager  (package>lock version)

---

### Post by jmjohn on 2008-10-11
Thanks all.  Does anyone know a way to skip just a particular update without locking the package?

Thanks in advance!

---

### Post by frankleeee on 2008-10-11
> **jmjohn said:**
> Thanks all.  Does anyone know a way to skip just a particular update without locking the package?

Thanks in advance!

When you get updates you can tick any you don't want off, then I think if you run sudo apt-get autoremove it removes them from the update manager. It may be sudo apt-get autoclean I don't remember but these are both valuable commands for removing old packages after updates.

---

### Post by jmjohn on 2008-10-15
Once I ran apt-get install to install a different package, it automatically removed the previous broken package.

Thanks all!
-glass.dimly

---

### Post by Church on 2010-01-29
And how can i lock software version from CLI? And so that apt-get would honour it too?
So far on ubuntu 9.10 if i locked in synaptics package manager particular xserver-xorg-intel version i manually downgraded to, apt-get -s upgrade still shows, that it wants to upgrade it.

---

