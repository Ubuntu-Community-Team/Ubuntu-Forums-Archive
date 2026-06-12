---
title: "Dual-Boot Ubuntu with Fedora?"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by CsG_kieran_2 on 2010-11-12
hey, I am looking to Dual-Boot Ubuntu and Fedora but I have no idea how to. seen some stories about fedora deleting ubuntu so...
any info/help?(32bit)

Thanks :KS

---

### Post by garvinrick4 on 2010-11-12
If you have Ubuntu install already make a partition for fedora in gparted and when you install choose manual install and put your / in that partition # and then if you have over
2 gig or more of Ram ignore swap. If under 2 gig make a swap partition. About 2 times the size of installed ram and put swap in that partition #. Format / in ext4 and when it comes to grub just choose not to install any grub at all.( Fedora uses grub-legacy and Ubuntu grub2.) When through installing boot into Ubuntu first and; 
```
sudo update-grub
```Will make new grub config and os-prober will find fedora install and put in boot menu and config file.
Fedora uses a program called anaconda I believe to install with and pretty straight forward.

---

### Post by CsG_kieran_2 on 2010-11-13
Ah, Thanks you the man (or woman) :popcorn:

---

