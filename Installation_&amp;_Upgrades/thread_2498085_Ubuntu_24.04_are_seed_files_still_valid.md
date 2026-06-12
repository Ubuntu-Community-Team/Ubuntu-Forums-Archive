---
title: "Ubuntu 24.04: are seed files still valid?"
date: 2024-05-29
forum: Installation &amp; Upgrades
---

### Post by couki72 on 2024-05-29
Porting an Ubuntu 20/22 custom install to Ubuntu 24: previous seed files do not get executed.
Does Ubuntu 24 still support them? Or shall I port to autoinstall.yaml

Thanks

---

### Post by MAFoElffen on 2024-05-29
No it does not. Not since 22.10.

Since 23.04, Desktop switched over to autoinstall.yaml.

After you boot the Desktop installer ISO image using Try, look under the path '/snap/ubuntu-desktop-bootstrap/<version>/bin/subiquity/examples' for the 24.04 autoinstall yaml examples.

---

