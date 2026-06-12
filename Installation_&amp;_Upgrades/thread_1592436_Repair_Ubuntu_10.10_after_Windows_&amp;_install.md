---
title: "Repair Ubuntu 10.10 after Windows &amp; install"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by lmicu on 2010-10-10
I had installed a Ubuntu 10.10 on /dev/sda1
I made another partition /dev/sda2 and I formated to ntfs
Extended partition is on /dev/sda3
The swap is on /dev/sda5

I installed Windows on /dev/sda2 and now I can't repair my grub (that would be grub2)

I booted with Live Cd (10.10) and I have no idea what to do.

---

### Post by lmicu on 2010-10-10
Bump

---

### Post by oldfred on 2010-10-10
If it is a new install of 10.10 you have grub2. Reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

While in the LiveCD, open terminal and run:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by sikander3786 on 2010-10-10
Please see here.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by lmicu on 2010-10-10
This worked!


Thank you, OLDFRED!

---

### Post by lmicu on 2010-10-10
TKS, for the post!

Long live the Linux community!

---

