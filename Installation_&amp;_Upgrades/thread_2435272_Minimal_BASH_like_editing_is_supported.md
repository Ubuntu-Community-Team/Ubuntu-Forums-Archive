---
title: "Minimal BASH like editing is supported"
date: 2020-01-18
forum: Installation &amp; Upgrades
---

### Post by ObscurityPrince on 2020-01-18
.

---

### Post by ubfan1 on 2020-01-18
From the live CD, take a look at the EFI partition and the file  /EFI/ubuntu/grub.cfg.  It probably uses a UUID for your (old) Ubuntu root, which changed when you resized.  Use blkid command in a terminal to get all the UUIDs, locate the one for your Ubuntu root, and edit that one into the /EFI/ubuntu/grub.cfg . Or maybe all it takes is to reinstall grub.

---

### Post by ObscurityPrince on 2020-01-19
Thanks ubfan1 for the reply. How though do I access the file /EFI/ubuntu/grub.cfg from the live CD?

---

### Post by ubfan1 on 2020-01-19
Mount the EFI partition (Use /mnt as a mount point unless it's not empty, otherwise, just make a directory under /mnt and mount there). Assuming your EFI is on sda1 below.
sudo mount -tvfat /dev/sda1 /mnt
Then you should see the EFI directory under /mnt,:  
ls /mnt
EFI
So change default directory to 
cd /mnt/EFI/ubuntu
and edit the grub.cfg file.

---

### Post by ObscurityPrince on 2020-01-21
.

---

