---
title: "Installing agave returns error, it can then not be installed or removed."
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by AkuTenshi on 2008-06-27
I recently tried to install agave (sudo apt-get install agave), and it went fine until it tries to cenerate a new icon cache, at which point it crashes dpkg with error code 1:
```

Setting up agave (0.4.3-2) ...
gtk-update-icon-cache: The generated cache was invalid.
dpkg: error processing agave (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 agave
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Other programs install/uninstall fine. Tried manually regenerating the icon cache, but to no avail. Any help?

---

