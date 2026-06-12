---
title: "Ubuntu 24.10 beta won't install on Virtualbox 7.1"
date: 2024-09-23
forum: Installation &amp; Upgrades
---

### Post by heynnema on 2024-09-23
Ubuntu 24.04
Virtualbox 7.1

The Ubuntu 24.10 beta won't install on a Virtualbox 7.1 VM. The installer just freezes. It'll freeze at different points if I deselect the full installation, or if I deselect the addition of various media/wifi optional installs.

It freezes during the "copying files" portion, but I don't see the VB status icons indicate that any VM disk activity is occurring.

Has anybody gotten the beta to work in a VM?

---

### Post by heynnema on 2024-09-23
Turns out that Virtualbox doesn't like hostnames with spaces or special characters.

Problem solved.

---

### Post by 1fallen on 2024-09-23
Sorry I have not used VB for years, but use QEMU/KVM for all my VM's and all Buntu's install nicely there.

Not what you asked about but offered as another possible.

EDIT I see you now have it solved. ;)

---

### Post by ActionParsnip on 2024-09-24
Please mark as solved if the issue is gone

---

