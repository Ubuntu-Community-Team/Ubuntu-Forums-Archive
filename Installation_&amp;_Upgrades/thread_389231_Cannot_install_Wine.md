---
title: "Cannot install Wine"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Scyphus on 2007-03-20
Running Ubuntu 6.10. Opening up the Synaptic package manager, selecting Wine for installation, and I get this error message:

wine:
  Depends: libgphoto2-2 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed
  Depends: libgphoto2-port0 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed

But those packages are already installed.

I tried uninstalling them and then installing Wine, and instead I got this:

wine:
 Depends: libgphoto2-2 but it is not going to be installed
 Depends: libgphoto2-port0 but it is not going to be installed

What do I do?

---

### Post by steevz on 2007-03-20
I'm having the exact same problem. Any help would be great.

---

### Post by zvacet on 2007-03-20
Install missing dependencies with synaptic.You have all repositories open do you?

---

### Post by Fuzzban on 2007-03-20
Funny, I just had that same problem but luckily I fixed it. First off it gave me the same problems when I installed it though Synaptic ( System>Administration>Synaptic Package Manager). My solution was to go to Synaptic Package Manager and uninstall it (if installed), libgphoto2-port0 version 2.2.1, and then dl the updated one, 2.3.0, from:

[https://launchpad.net/ubuntu/edgy/i3...0ubuntu3~edgy2](https://launchpad.net/ubuntu/edgy/i3...0ubuntu3~edgy2)

Then libgphoto2-2 2.3.0 from:

[https://launchpad.net/ubuntu/edgy/i3...0ubuntu3~edgy2](https://launchpad.net/ubuntu/edgy/i3...0ubuntu3~edgy2)

Remember to download the .deb file, not source file unless you know what your doing. That should do it.

---

### Post by steevz on 2007-03-22
I updated and upgraded and then it worked fine.

---

