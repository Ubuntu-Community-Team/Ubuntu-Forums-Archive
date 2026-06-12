---
title: "Replace other distro on dual boot"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by Bartly on 2010-01-30
I have a laptop dual booted with Win 7 and Fedora. I want to replace Fedora with Ubuntu. Is it safe to simply delete all the non-ntfs partitions during the Ubuntu install? I just don't want to whack Windoze as I depend on it ofr work. THe current partitions are:'
dev/sda1  ntfs  104 mb
dev/sda2  ntfs  58336 mb
dev/sda5  ext4  209 mb
/dev/sda6 unknown 54196  mb
dev/sda3  fat32  7176 mb
 
Thanks

---

### Post by kansasnoob on 2010-01-30
> **Bartly said:**
> I have a laptop dual booted with Win 7 and Fedora. I want to replace Fedora with Ubuntu. Is it safe to simply delete all the non-ntfs partitions during the Ubuntu install? I just don't want to whack Windoze as I depend on it ofr work. THe current partitions are:'
dev/sda1  ntfs  104 mb
dev/sda2  ntfs  58336 mb
dev/sda5  ext4  209 mb
/dev/sda6 unknown 54196  mb
dev/sda3  fat32  7176 mb
 
Thanks

I don't know what the FAT32 partition is???????????

---

### Post by Bartly on 2010-01-30
> **kansasnoob said:**
> I don't know what the FAT32 partition is???????????
 
I don't either but it may be a recovery or HP tools or something. I'll leave that one alone.

---

### Post by Bartly on 2010-01-30
To answer my own question, it worked fine, to my relief. I deleted the patitions that were not ntfs or fat32, created swap, root, and home partitions,  and the grub loader installed fine and everything works. Yay Ubuntu! :D

---

