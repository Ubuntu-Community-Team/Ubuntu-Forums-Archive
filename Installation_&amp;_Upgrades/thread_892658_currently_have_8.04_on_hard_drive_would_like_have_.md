---
title: "currently have 8.04 on hard drive would like have half allocated for windows XP"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by mitchelljj on 2008-08-17
Hi,

I currently have Ubuntu 8.04 on entire hard drive and I would like to have half allocated for windows XP, and then install windows XP on the newly allocated half.

How do I do this?

Thanks,

John

---

### Post by logos34 on 2008-08-17
shrink hardy down using gparted on the ubuntu live cd.

Install xp in the unallocated space (full not 'quick' format)

Since windows will overwrite grub on the mbr (no way around it), restore grub using the live cd (see link my signature).

Add [windows entry]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu") to menu.lst and [fstab]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20%28Hardy%20Heron%29")

good luck!

also: get **fs-driver** so you can access linux from xp

---

