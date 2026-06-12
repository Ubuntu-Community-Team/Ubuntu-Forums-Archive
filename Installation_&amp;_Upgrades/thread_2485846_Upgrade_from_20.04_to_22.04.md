---
title: "Upgrade from 20.04 to 22.04"
date: 2023-04-11
forum: Installation &amp; Upgrades
---

### Post by weswitt on 2023-04-11
using do-release-upgrade to upgrade from 20.04 to 22.04 i review the packages that will be removed, installed and upgraded. i see a line saying "Remove: qemu-kvm". why is the installer wanting to remove KVM from my system? i'm using it and have vms running.

---

### Post by deadflowr on 2023-04-11
Because it is now provided by qemu-system-X, X being which ever qemu-system package you are going to be running, typically qemu-system-x86

Provided means it's built into the package.

---

### Post by weswitt on 2023-04-11
thanks, that makes sense

---

