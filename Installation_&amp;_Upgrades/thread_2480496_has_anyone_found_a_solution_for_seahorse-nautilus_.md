---
title: "has anyone found a solution for seahorse-nautilus on ubuntu 22.10"
date: 2022-10-31
forum: Installation &amp; Upgrades
---

### Post by jlbotto on 2022-10-31
it is not possible to install the extension seahorse-nautilus on ubuntu 22.10, so no way to encrypt/decrypt a file.
Has anyone found a workaround?

---

### Post by Dennis N on 2022-10-31
What happened to the extension?
You could always fall back to using the terminal and the gpg command to encrypt or decrypt.

---

### Post by deadflowr on 2022-10-31
> What happened to the extension?
It's was among of bunch of extensions removed because of the upgrade to nautilus 43:
[https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1984233]("https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1984233")

---

### Post by Dennis N on 2022-11-01
> **deadflowr said:**
> It's was among of bunch of extensions removed because of the upgrade to nautilus 43:
[https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1984233]("https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1984233")
Thanks for the link. I see a fix has been released.
```
Comment: Incompatible with new nautilus based on GTK4 and blocks library transition;
...
Changed in seahorse-nautilus (Ubuntu):
status: 	New &#8594; Fix Released 

```

---

