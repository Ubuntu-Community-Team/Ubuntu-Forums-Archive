---
title: "replace Opensuse with ubuntu on dual boot with WINX P"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by Scott_karsten on 2010-04-16
Existing dual boot with Opensuse 11.2 KDE and WIN XP PRO. Tried using Ubuntu 9.10 Live CD to format Opensuse partition and install Ubuntu over Opensuse. Screen locks up, must cold boot system. Checksum number matches correctly. Can I use WIN XP CD to repair boot loader & then install Ubuntu? Any and ALL help is GREATLY appreciated. Thank you [:~)

---

### Post by tom4everitt on 2010-04-17
Actually, all you have to do is to install ubuntu on the partition you had opensuse on. Then ubuntu will automatically install a boot loader (grub2) and it will also find windows xp. So although you could fix the windows boot loader before installing ubuntu, there's no point really. It will just be overwritten again anyway. 

So just:

1. Start the computer from the ubuntu live cd.
2. Choose install to hard drive
3. Choose manual installation, so you can choose where exactly to install it.
4. Done.

---

