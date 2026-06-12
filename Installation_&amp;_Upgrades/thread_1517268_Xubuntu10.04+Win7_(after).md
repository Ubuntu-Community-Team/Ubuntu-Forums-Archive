---
title: "Xubuntu10.04+Win7 (after)"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by magicmax0 on 2010-06-24
I already have Xbuntu installed on /dev/sda1/ but i would like to install Windows 7 now on /dev/sdb2. My goal is to manually set boot priority in my BIOS to boot from either one. So my question is, by installing Windows 7 on sdb2 will i still be able to boot from sda1 if i select it as primary boot drive in BIOS, or will it still wipe my MBR and Grub2 on sda1?

---

### Post by zvacet on 2010-06-25
It will wipe grub and you will have to reinstall it.See [this.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by magicmax0 on 2010-06-25
Thats what i figured, i have come accross that guide before but figured if i had it on a whole other drive i might not have to do it. Thanks.

---

