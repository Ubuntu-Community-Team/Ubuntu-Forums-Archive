---
title: "Apt-get how to get list of installed packages"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by sistoviejo on 2007-06-26
Hello,
I have two questions about apt-get:
Is it possible to get a list of installed packages?
Is it possible to see whether a package has already been installed or not?

---

### Post by mikewhatever on 2007-06-26
You can do that in Synaptic. An installed package is marked green. Search for whatever package you need.

---

### Post by az on 2007-06-26
> **sistoviejo said:**
> Hello,
I have two questions about apt-get:
Is it possible to get a list of installed packages?
Is it possible to see whether a package has already been installed or not?

to list installed package:

dpkg -l

To see if a package is installed:

dpkg -l |grep package

---

### Post by sistoviejo on 2007-06-26
> **mikewhatever said:**
> You can do that in Synaptic. An installed package is marked green. Search for whatever package you need.

i forgot to say... no access to gui.
i'm accessing through ssh.

---

### Post by sistoviejo on 2007-06-26
> **az said:**
> to list installed package:

dpkg -l

To see if a package is installed:

dpkg -l |grep package

thanks!

---

