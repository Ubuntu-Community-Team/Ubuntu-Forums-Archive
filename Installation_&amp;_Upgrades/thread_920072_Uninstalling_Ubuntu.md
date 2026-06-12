---
title: "Uninstalling Ubuntu"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by nosactivated on 2008-09-14
I am running Vista first of all. I installed Ubuntu with the disc with no problem. But I am unable to uninstall it from the dual boot or from the hard drive. I have tries the Add/Remove programs with no luck. When I use the add/remove tools I get nothing that happens. I manually deleted the files from the hard drive but I still get the dual boot options. I am sure that Ubuntu is part of the MBR now. I can not find any info on how to remove Ubuntu anywhere in the forums. OR I am just missing it. Also tried to do a search, but no luck. So if anyone here can help. That would be grateful.

---

### Post by Pumalite on 2008-09-14
Erase the partition with Gparted. Then fix your Windows MBR with Super Grub:
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
Burn to disk and boot from it.

---

