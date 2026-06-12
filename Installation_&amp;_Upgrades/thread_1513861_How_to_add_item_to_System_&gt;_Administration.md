---
title: "How to add item to System &gt; Administration"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by GeertVc on 2010-06-20
Hi,

I just upgraded my Ubuntu 9.10 to Ubuntu 10.04.  Part of the Ubuntu 9.10 installation was GParted (version 0.4.5) and I saw, after upgrading to Ubutnu 10.04, there was a more recent version available: 0.5.1.

After installing that version, GParted was still part of the **System > Administration** menu (just as it was before).

But then I saw the version 0.6.0 of GParted was recently released and there was also a .deb distro available.

After downloading and installing the 0.6.0 version of GParted, the item GParted disappeared from the **System > Administration** menu and appeared in another menu (**Applications > System Tools**).

My question: how can I get GParted back as part of the **Systems > Administrations** menu?

Best rgds,
--Geert

---

### Post by dv3500ea on 2010-06-20
Right click on the Applications menu and click Edit Menus.
You can add a new item under System -> Administration from here and also remove the item from Applications -> System Tools.

---

### Post by wilee-nilee on 2010-06-20
Sometime installs don't show up do the right click on menu and see if it is actually there tick it of then on, if it's not there then build a new launcher as suggested.

---

### Post by GeertVc on 2010-06-21
> **dv3500ea said:**
> Right click on the Applications menu and click Edit Menus.
You can add a new item under System -> Administration from here and also remove the item from Applications -> System Tools.

That is indeed working fine.  Thanks!

Best rgds,

--Geert

---

