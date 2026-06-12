---
title: "Unable to upgrade from 22.10 to 24.04.1"
date: 2024-09-03
forum: Installation &amp; Upgrades
---

### Post by vs-punn on 2024-09-03
When I click on upgrade Ubuntu to 24.04.1, the window opens for downloading two files. After that the window goes off, and nothing happens.
My current version is 22.10

---

### Post by Dennis N on 2024-09-03
> **vs-punn said:**
> When I click on upgrade Ubuntu to 24.04.1, the window opens for downloading two files. After that the window goes off, and nothing happens.
My current version is 22.10

22.10 is unsupported for normal upgrading. Run sudo do-release-upgrade for a link with upgrade information

```
dmn@Tyana-vm:~$ sudo do-release-upgrade

Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

```

---

