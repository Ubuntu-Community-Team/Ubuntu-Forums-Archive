---
title: "Keeping package archive when reinstalling."
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by yacwroy on 2012-02-16
Short:
=====
Can I just copy my current /var/cache/apt/archives to the same location after I reinstall, and save having to download ~4GB?

Do I need to also copy /var/cache/apt/pkgcache.bin & srcpkgcache.bin? Or will this break things?



Details:
=======
I recently installed Ubuntu 11.10 and downloaded a few GB of packages.

I tried out Cinnamon and XFCE (shell and unity are too inflexible for me and can't be set up to be efficient). I now prefer XFCE (even to Gnome2).

However, Gnome3 or 11.10 keeps causing micropauses (cursor freezes for a second or so every few minutes) and there are other glitches. This happened even before trying alternate DEs.

I now have Xubuntu 11.10 downloaded.

Also, I actually have /var/cache/apt/archives as a symlink to a separate partition - it's working fine.



Thanks,
Simon.

---

### Post by zvacet on 2012-02-17
If all content of /var/chache/apt/archives is in one folder you can install those packages after reinstall.Of course folder with /var/chache/apt/archives will be on some safe place ( like usb or something similar).When you are finish with reinstall you can put that folder for example in your home and go inside of it and run

```
sudo dpkg -i *deb
```
That will install all your packages.

---

### Post by yacwroy on 2012-02-17
That could be quite handy, thanks.


At the moment, though, I don't want to install every package in my archive (there'll be many from gnome 3 & cinnamon that I don't want).

But when I do ask apt-get (or synaptic, etc..) to install something, I want it to use the local package I downloaded previously (assuming it's the same one).

Will this automatically work if I just copy the package files back into the archive folder? Or does Ubuntu have a list of downloaded packages that it checks and that I'll need to update? (eg: pkgcache.bin)

---

### Post by cortman on 2012-02-17
> **yacwroy said:**
> That could be quite handy, thanks.


At the moment, though, I don't want to install every package in my archive (there'll be many from gnome 3 & cinnamon that I don't want).

But when I do ask apt-get (or synaptic, etc..) to install something, I want it to use the local package I downloaded previously (assuming it's the same one).

Will this automatically work if I just copy the package files back into the archive folder? Or does Ubuntu have a list of downloaded packages that it checks and that I'll need to update? (eg: pkgcache.bin)

I believe apt-get will install from the archive by default, if it's there. But you can try it out and see.

---

