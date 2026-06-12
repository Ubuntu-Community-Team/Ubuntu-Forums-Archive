---
title: "Upgrade to 24.04 removed opendkim"
date: 2024-10-17
forum: Installation &amp; Upgrades
---

### Post by aathan on 2024-10-17
My ubuntu system had opendkim installed via apt.

Upon completion of the 24.04 upgrade, opendkim was no longer an installed package. I had to instead re-install via apt. dpkg -l reported opendkim as "rc"

If that's not expected, please let me know how to gather forensics and where to submit them.

---

### Post by grahammechanical on 2024-10-18
If a software package is not in the official Ubuntu repositories then the upgrade process cannot upgrade that application as part of the upgrade to the new version. All the files and libraries relating to that application might be marked as obsolete files. During an upgrade from one version to the next we might be asked to authorise the removal of obsolete files. If we authorise the removal of obsolete files then that would explain how this software was removed.

Regards

---

