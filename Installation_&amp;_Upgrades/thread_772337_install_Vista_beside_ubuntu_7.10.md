---
title: "install Vista beside ubuntu 7.10"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by guthar on 2008-04-28
Hi,

I had already installed Ubuntu Gutsy Gibbon 7.10 and I would like to install Vista Home Premium. I created free partition "ntfs" by Gparted. And now if I try to install Vista, it will overwrite boot loader. How to avoid this problem ?

Regards,
Paul

---

### Post by twright on 2008-04-28
when you install vista it will break grub  all you need to do to repair it is use the ubuntu live CD and type "sudo grub-install /dev/sda" or "sudo grub-install /dev/hda"

---

