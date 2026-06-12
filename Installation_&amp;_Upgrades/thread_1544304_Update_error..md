---
title: "Update error."
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by hyderpotter on 2010-08-02
When I try and update I keep getting errors.

```
Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by mikewhatever on 2010-08-02
System->Admin->Software Sources.
Uncheck the cdrom box and reload.

---

### Post by MasterGamerJK on 2010-08-02
try above and check proxy config/other network related settings

---

