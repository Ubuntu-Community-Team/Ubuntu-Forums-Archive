---
title: "Dual boot problems"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by saket3143 on 2010-04-05
This s my first post 
i am having problems installing ubuntu after win 7
the partitioner does not recognize the boot loader but the partitions are perfectly mountable
it only shows the hdd without recognizing ntfs partitions

---

### Post by oldfred on 2010-04-05
Did you use the windows tools to shrink the windows partition and reboot windows. After shrinking windows wants to run chkdsk to verify its new size and Ubuntu or gparted will not mount NTFS drives that have the chkdsk flag set.

---

### Post by whashtonjr on 2010-04-05
I'm having the same problem. Initially the install worked but a GRUB update had a problem. I tried to reinstall but since then have not been able to get the installer to recognize the unallocated partition I create (have removed and recreated). This is without rebooting windows but booting from the DVD. I'm assuming a problem with Windows disk management. Wubi does not work either.

---

