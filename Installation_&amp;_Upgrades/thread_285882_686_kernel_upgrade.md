---
title: "686 kernel upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by wey97 on 2006-10-27
I just downloaded the linux-image-686 kernel upgrade, installed it, and rebooted.  I then uninstalled the old linux-image-386 image (don't worry it's on VM so I can reinstall if it gets hosed)

How can I verify that the new 686 kernel is running?  I don't see any config for hyperthreading or multiple processor support.

Also, none of the packages titled kernel-image-2.*-686 or kernel-headers-2.*-686 were installed.  What is the difference between these packages and the linux-image-686 package?

What about linux-restricted-modules-686?

I know this is asking a lot, but I'm fairly new to Ubuntu.

Thanks

---

### Post by tronica on 2006-10-27
to see if what kernel your running type this in your terminal


> uname -r

---

### Post by wey97 on 2006-10-27
Ok thanks, and I forgot you get the choice of which kernel to boot into.

---

### Post by uqbar on 2006-10-27
> **wey97 said:**
> I just downloaded the linux-image-686 kernel upgrade, installed it, and rebooted.  I then uninstalled the old linux-image-386 image (don't worry it's on VM so I can reinstall if it gets hosed)


Maybe I'm wrong as I'm new to Ubuntu, but I have read on the [package database]("http://http://packages.ubuntu.com/edgy/base/linux-image-686") that linux-image-686 is obsoleted by linux-image-generic.
So, if I needed to go from 386 to 686, which package should I install?
Thanks.

---

### Post by wey97 on 2006-10-27
> **uqbar said:**
> Maybe I'm wrong as I'm new to Ubuntu, but I have read on the [package database]("http://http://packages.ubuntu.com/edgy/base/linux-image-686") that linux-image-686 is obsoleted by linux-image-generic.
So, if I needed to go from 386 to 686, which package should I install?
Thanks.

It means just what it says as far as I know.  In the "edgy" release, the 686 package is deprecated by the "generic" package which should be used.

---

