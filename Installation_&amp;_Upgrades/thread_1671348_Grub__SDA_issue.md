---
title: "Grub / SDA issue"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by xtremezj on 2011-01-19
I got a brand new laptop today with W7 Ultimate on it, and decided to dual boot with ubuntu 10. Long story short i got ubuntu 10 up and running but Windows is now missing from grub. My setup is:

sda1 - recovery partition, ntfs
sda2 - win 7 , ntfs
sda3 - ubuntu, ext4
sda4 - swap

Everything shows up in grub, except sda2. It shows "Vista Loader" but that is the recovery program on sda1.

I have tried "[COLOR=#FF0000]sudo update-grub2" already, any other ideas?
[/COLOR]

---

