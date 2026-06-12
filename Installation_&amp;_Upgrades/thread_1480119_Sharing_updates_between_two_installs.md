---
title: "Sharing updates between two installs"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by rolnics on 2010-05-11
I'm planning to have two installs on the same pc, so I can break / test one and still have a usable system.

I've got my partitions setup so I have a separate  /home for both installs to share, but how do I share the updates? I'm going to use clonezilla to copy the working (/) partition, but how can I use the updates for both installs. I'm just trying to save downloading twice if possible. Is there a way to copy or use the updates applied in one partition to the other? Does apt save the updates somewhere?

---

### Post by hatalar205 on 2010-05-11
All updates are saved in var/cache/apt/archives

You must copy them in the same directory in the other partition. But, in the other partition, you aren't allowed to copy them to that directory. So, **Alt+F2** and write **sudo nautilus** and copy them. Then begin to update your system.

---

