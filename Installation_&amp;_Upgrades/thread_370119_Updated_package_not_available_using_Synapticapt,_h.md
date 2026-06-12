---
title: "Updated package not available using Synaptic/apt, how to sync if I install it myself?"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by monocongo on 2007-02-25
There is a new version available of a software package which I already have installed using Synaptic, however when I look for the latest available version using Synaptic it only displays the previous version.  If I build and install the new version myself then how will Synaptic (or apt) know what version I have installed?  When you make an installation like this "by hand" is there any way to sync with Synaptic/apt, or do you lose the ability to manage a package once you step outside the realm of these package managers for a certain package?

---

### Post by zvacet on 2007-02-28
Everything that you install you will find in synaptic.How synaptic know version?You told it by installing.

---

### Post by monocongo on 2007-02-28
I built and installed a new version of a package from source (configure, make, make install) and now when I look for it in Synaptic/Adept I still see the old version listed as the installed version.  Is there an apt command I can run which will update the installed package database with the new version of this package?

---

### Post by actuary286 on 2007-03-01
Synaptic can only handle software installed from .deb files. Software built from source will not appear in Synaptic. One alternative is [checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/"), a replacement for ```
make install
``` that attempts to build a native package (.deb) that you can then install and have Synaptic track. I haven't personally used the software, but it is reccommended by Chess Griffin of the [Linux Reality]("http://www.linuxreality.com") podcast.

Checkinstall is in the universe repository.

---

