---
title: "Ext HDD does not connect when backup selected in 14.04"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by mushistereck on 2016-06-05
Whe I try to do a backup to the ext HDD it sdays it cannot do it until the drive is connected. How do I connect? 
Using 14.04 and formatted NTFS. Tried ext4 and Fat 32 but no joy

---

### Post by DuckHook on 2016-06-05
In Linux, drives must be mounted before they are accessible as file systems. Most external drives will mount if you try accessing them with Nautilus. Just click on the icon representing the drive in your file manager.

Unless you are accessing the drive from Windows, it is not wise to keep it formatted as NTFS. This file system is not native to Linux and there is less support for it. ext4 is the best choice, although there are now many others, most of which also lack the same extent of tools that exist for ext4.

---

### Post by mushistereck on 2016-06-05
Tried ext4. No change. When I start Backup to the ext drive it says"Drive is not connected". It shows up in gparted OK.

---

### Post by DuckHook on 2016-06-05
> **mushistereck said:**
> Tried ext4. No change. When I start Backup to the ext drive it says"Drive is not connected". It shows up in gparted OK.

But did you ***mount*** it first?

> **DuckHook said:**
> In Linux, drives must be mounted before they are accessible as file systems. Most external drives will mount if you try accessing them with Nautilus. Just click on the icon representing the drive in your file manager...

---

