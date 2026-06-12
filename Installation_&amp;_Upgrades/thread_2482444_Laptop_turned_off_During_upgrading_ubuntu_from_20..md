---
title: "Laptop turned off During upgrading ubuntu from 20.04 to 22.04"
date: 2022-12-31
forum: Installation &amp; Upgrades
---

### Post by himal007 on 2022-12-31
I was upgrading my ubuntu from 20.04 to 22.04. But while installing or unpacking newly downloaded files my laptop shutdown due to power failure. 
And now It is not turning on it is freezing  with following text on screen:

""Sgx disabled by bios
/dev/sda2:clean,457670/61022208 files , 14713444/244059136 blocks""

---

### Post by oldfred on 2022-12-31
Those two lines are normal, just comment on setting in UEFI/BIOS and showing no error on sda2.

Do you only have one system?
If so can you press escape if UEFI or press & hold shift key right after vendor logo & before grub would normally show, to get grub menu?
And then for any kernel shown, can you boot recovery mode?

Do you have good backups? Required before any major change.

Do you have live installer, so you can boot it and make repairs? You should always have a working live installer for the current version installed.

---

### Post by himal007 on 2023-01-01
Thanks sir. I made a pendrive bootable and deleted previous version and installed new one by erasing disk. Now its working fine

---

