---
title: "view difference: ubuntu-desktop and other packages"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by kabanta on 2008-04-23
When I upgrade or reinstall the OS, it is useful to know what additional packages I have installed in the old/existing OS so that I can quickly install them in the new OS installation. Any tips how to do this?

I believe the default set of packages installed is **ubuntu-desktop**, so it would be nice to be able to see a listing of all my installed packages that are *not* part of **ubuntu-desktop**.

Alternatively, is there a way to sort the list of installed packages by *date installed*?

---

### Post by dstew on 2008-04-24
You can get the information you want, but I don't know how to do it easily. You can check in synaptic for installed packages. To get a list of all your installed packages you can do```
dpkg -l
```Ubuntu-desktop is all the packages for the graphical interface, but there are lots of packages in the base system too.

---

