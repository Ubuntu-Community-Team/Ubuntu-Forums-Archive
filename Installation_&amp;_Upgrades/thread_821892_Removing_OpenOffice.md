---
title: "Removing OpenOffice"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by HybridTheory on 2008-06-07
Ok I looked around on the forms on how to do this and it says to remove Ubuntu-Desktop...and I already did before I started looking but I can still start Openoffice any clues?

thanks

---

### Post by avtolle on 2008-06-07
Go to Synaptic and check each installed OO app for complete removal, then after they are all marked, click on apply. Hopefully, that will do it.

---

### Post by aysiu on 2008-06-08
Removing *ubuntu-desktop* doesn't really remove anything. *ubuntu-desktop* is just a pointer to all the default packages in Ubuntu. Removing the pointer doesn't remove the packages it points to.

If you want to remove OpenOffice, then paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove openoffice.org-base-core openoffice.org-core
```

---

### Post by stchman on 2008-06-08
> **HybridTheory said:**
> Ok I looked around on the forms on how to do this and it says to remove Ubuntu-Desktop...and I already did before I started looking but I can still start Openoffice any clues?

thanks
If using Hardy do this at a terminal:

```
dpkg -l | grep openof
```

This will show you all the Openoffice.org 2.4 packages.

Remove all these packages and OO will be completely uninstalled.

---

