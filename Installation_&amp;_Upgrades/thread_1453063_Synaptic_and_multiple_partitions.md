---
title: "Synaptic and multiple partitions"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by noanker on 2010-04-12
I am running 9.10 on a machine with more partitions than just the one which comes with Ubuntu. This way I can upgrade the OS without everything being erased, such as the home directory.

If I use Synaptic to download and install a new package, can I direct it to install the package in a partition other than the one which holds the Ubuntu kernel?? I have been told that Synaptic will only install in the same partition as the kernel.

---

### Post by MooPi on 2010-04-12
I have just read the man pages for apt-get which is the underlying utility for the GUI that is Synaptic. It does not allow for alternate install locations.

---

### Post by omegvermelho on 2010-04-12
Even if you´re using multiple Debian/Ubuntu partitions i seriously doubt that u can use Synaptic to Manage the Package(s) for all eligible partitions...

---

### Post by srs5694 on 2010-04-12
Underneath Synaptic and apt-get is dpkg, and dpkg *does* permit this, using the --root option. Read the dpkg man page for details. If you don't understand it from that information, you should not be messing with such options.

---

