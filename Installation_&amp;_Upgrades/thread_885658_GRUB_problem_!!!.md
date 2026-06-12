---
title: "GRUB problem !!!"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by sagarnatekar on 2008-08-10
Hi guys ! I have win xp and ubuntu 7.10 installed on my pc. The problem is, the loader doesn't show windows xp in the boot menu....and so I have to compulsorily access ubuntu even when I don't want to :confused:. I tried changing the menu.lst file and added an option for xp,but my pc reboots when I select it. I have 3 primary partitions (1 for xp[C:\] and 2 for linux-ext3 and swap) and 1 extended partition[D:\]. What must be the problem ? The data on the drives is not affected. Do I have to reinstall xp ?

---

### Post by Pumalite on 2008-08-10
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by sagarnatekar on 2008-08-10
OK...but what to do next ? :(

---

### Post by Pumalite on 2008-08-10
Copy and paste here

---

