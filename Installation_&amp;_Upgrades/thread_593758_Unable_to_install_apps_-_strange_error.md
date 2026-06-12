---
title: "Unable to install apps - strange error"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by 3pleT on 2007-10-27
I was installing the dependencies of the latest build-essential package (I have installed Ubuntu 6.07 three days ago), During the installation of dpkg-dev, Package Installer just crashed with no warnings and I couldn't start it anymore (it always does the same thing). I tried to run Synaptic, but it returns this error:

```
E: Malformed 3rd word in the Status line
E: Error occurred while processing libc6 (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

How can I fix this?
I'm new to linux, so please try to explain it the way I can understand.

---

### Post by 3pleT on 2007-10-27
Update:

I changed the line "Status:" of libc6 in /var/lib/dpkg/status but now I can't install things (installation failed + empty terminal). Please help...

---

