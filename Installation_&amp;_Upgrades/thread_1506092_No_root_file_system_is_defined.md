---
title: "No root file system is defined"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Moizkhanmalik on 2010-06-10
So I have an external hard drive (wd passport) that I want to install ubuntu on. I created 100gb partition via diskutility (fat32) and it seems I can't install ubuntu on this partition. Any ideas?

---

### Post by lwf92 on 2010-06-10
> **Moizkhanmalik said:**
> So I have an external hard drive (wd passport) that I want to install ubuntu on. I created 100gb partition via diskutility (fat32) and it seems I can't install ubuntu on this partition. Any ideas?

assuming you are using the advanced partition creator, what you need to do is create either a ext3 or ex4 (ext4 is newer) partition with the / mount point. keep in mind that any programs you install will appear in this partition so i would recommend you make the partition around 15-20 GB in size minimum. good luck with your installation.

---

### Post by Moizkhanmalik on 2010-06-10
Thanks, that worked but now I am getting a new error. At 93% or so, it is giving me the following prompt:

"Unable to install GRUB in /dev/sdb3"

"Executing 'grub-install /dev/sdb3" failed"

"This is a fatal error"

---

### Post by cbecker78 on 2010-06-10
Does your bios support booting from USB?  If it can't the installer may just be recognizing that fact and not allowing it...

---

