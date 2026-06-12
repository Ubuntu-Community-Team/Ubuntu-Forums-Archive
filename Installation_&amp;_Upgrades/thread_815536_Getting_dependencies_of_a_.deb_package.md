---
title: "Getting dependencies of a .deb package"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Anupama on 2008-06-01
Hi, I am working on a secure installer and implementing it on debian.
For this, I need to find the dependencies of a package (already installed or uninstalled) offline, I cant intercept the functioning of apt-get.

Is there such a functionality available?

What build-dep does is something different I figured out.

Thanks for your help in advance.

---

### Post by Partyboi2 on 2008-06-02
Couldn't you use Synaptic and select the package you are wanting to know the dependencies and then click on "Properties" then "Dependencies"

---

### Post by xerxesdaphat on 2008-06-02
> **Partyboi2 said:**
> Couldn't you use Synaptic and select the package you are wanting to know the dependencies and then click on "Properties" then "Dependencies"

Because a) he's not necessarily dealing with things in apt-get, he's dealing with any random deb package; and b) he's writing a piece of software, he needs proper output, not some frilly POS GUI.

---

### Post by Anupama on 2008-06-02
> **xerxesdaphat said:**
> a) he's not necessarily dealing

she's

> **xerxesdaphat said:**
> Because a) he's not necessarily dealing with things in apt-get, he's dealing with any random deb package; and b) he's writing a piece of software, he needs proper output, not some frilly POS GUI.

Ya right. I figured out apt-cache depends pkg-name is what i need.

But thanks for your help.

---

