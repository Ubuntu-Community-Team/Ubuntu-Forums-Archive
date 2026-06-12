---
title: "Can't access my old SSD from new Ubuntu 22.04 install"
date: 2023-01-26
forum: Installation &amp; Upgrades
---

### Post by Gottier on 2023-01-26
I bought a new SSD for installation of Ubuntu 22.04. I took the old SSD with Ubuntu 20.04 out of the computer. I can usually put an old HDD in a hard drive dock "toaster" and browse the contents, but when I put the old SSD in the toaster it doesn't automatically appear and let me have access to it. It doesn't even show up with lsblk for a few minutes, and when it does show up it looks like this:

sdb 8:16 0 0B 0 disk

This is a 1TB drive.

What can I do? I want to be able to copy files from the old drive to the new drive.

---

### Post by yancek on 2023-01-27
Did you remove the old drive with 20.04 on it before installing 22.04?  Is 20.04 the only OS on the old drive?  Do you see any more information on that drive when you run either:

```
sudo fdisk -l  sudo parted -l
```

Were you having any problems with the old drive?  Have you tried running fsck on the old drive partitions if you can see them?

---

### Post by Gottier on 2023-01-30
I think it was the dock, although not sure why. I tried putting the drive in a hard drive enclosure, and it instantly worked.

---

### Post by ActionParsnip on 2023-01-30
If all is well then please mark as solved

---

