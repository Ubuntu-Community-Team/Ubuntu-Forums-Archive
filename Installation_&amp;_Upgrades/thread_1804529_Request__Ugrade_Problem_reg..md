---
title: "Request : Ugrade Problem reg."
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by sriram.326 on 2011-07-14
hi,

I had installed Kubuntu10.10 and Ubuntu11.04 on two partitions of my hard disk sda1, sda3 resectively. Upon starting my computer a menu used to prompt me asking for which OS to boot. 
I had just upgraded Kubuntu 10.10 to 11.04.
And now the system is automatically booting Kubuntu11.04 directly without any  menu. Now how can i log into Ubuntu11.04.

Thanks in advance.

---

### Post by mikewhatever on 2011-07-14
Try running **sudo update-grub** from Kubuntu. That command should try to detect all installed OSs and add them to Grub's menu.

---

