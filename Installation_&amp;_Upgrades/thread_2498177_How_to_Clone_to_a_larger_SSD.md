---
title: "How to Clone to a larger SSD"
date: 2024-06-02
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2024-06-02
I'm running whole-disk encrypted Lubuntu 22.04 and I'm running out of disk space on my 240G SSD, so using Clonezilla I selected a proportionate disk-to-disk technique targeting a 480G drive.

I thought that this would expand my operating folders and home folder out to the full 480 G.

The new disk boots just fine, and when I lsblk it indeed shows a 480 G sda/sda1. So far, so good. But both df -h and nautilus/properties shows only 240G.

So,

1) Is there a way to expand the encrypted drive out to the full 480G?

2) If not, what trick in clonezilla am I missing that does the job properly.

3) Finally, I've also used, in straight Terminal,

sudo dd if=/dev/sda of=/dev/sdb bs=4M status=progress

Which does the job just fine when the target disk (/dev/sdb) is the same size.

I'm really trying to avoid a full install.

Any ideas?

Thanks!!

---

### Post by wjbmd48 on 2024-06-02
DUH. Figured it out; all I had to do was mount the drive on another system. The drive showed up as 240G encrypted and 240G unallocated. All I had to do was resize the encrypted part of the drive up to 480G in Gparted.

---

