---
title: "Installation of Ubuntu 10.04 stops"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by jlunse on 2010-05-13
I've downloaded 10.04 today and it works fine to boot the cumputer with Ubuntu. Then I start the installation and it first seems to work fine. But the installation just freeze/stops with progress bar like 45%. No error is displayed. I have tried this several times and with two different DVDs.

Any ideas?

---

### Post by zarap on 2010-05-13
I had the same issue installing lucid and found out it was because of my intel graphic chipset. I had to give an option to grub:
i915 modeset=1
With that I was able to start the live cd and to install.
Had some random X freezes afterwards and so I use the vesa driver on Lucid until there is a fix released.
more information: [wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")
I think there are some other graphik chipsets makeing troubles too, so better check out which one you have.

---

### Post by jlunse on 2010-05-15
**[COLOR="Red"]I successfully managed to install Ubuntu 10.04 by using Alternate disc.[/COLOR]**

I'm not sure why I couldn't install from the Live CD.

Anyway, really nice that it works just fine now:)

So, now I have Ubuntu 10.04 on all (2) cumputers at home.

//Jlunse

---

