---
title: "Partition 30gb HD"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by joelomar on 2007-01-30
Hello to all.  I have a 30gb Hard Drive that I want to put Ubuntu on.  The HD will be installed on a Dell LAtitude D610.  

If the HD is only going to be used for Ubuntu, does it make sense to create a /home partition in FAT32?  If not, should I just let the installer prepare the partitions as it wants?

---

### Post by meng on 2007-01-30
No it doesn't make sense to use FAT32, not even if you're going to share that space on a home network. If you let the installer prepare the partitions, however, it won't create a separate /home automatically. So do it manually, but set /home to ext3 (or other Linux-friendly FS if you have a strong preference).

---

