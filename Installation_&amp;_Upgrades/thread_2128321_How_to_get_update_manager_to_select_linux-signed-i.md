---
title: "How to get update manager to select linux-signed-image files for kernel update"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by mathias j sagartz on 2013-03-22
I've just installed 12.04LTS on my relatively new desktop.  The system is set to duel boot with Windows 8, uses UEFI, and secure boot is enabled.  It seems to be working well now as long as I use a kernel version that is signed with Canonical's UEFI signing key.   The repositories have both signed and unsigned versions of kernels available but Update Manager seems to pick the unsigned versions.  Is there a way to have it automatically choose the signed kernel version for update or do I have to update kernels outside of Update Manager?

---

### Post by gifford on 2013-03-22
Use synaptic for the updates. Just type in UEFI and it will bring up Canonical's signed version of the kernels.

---

