---
title: "getting alert  /dev/disk/by-uuid/ &lt;my uuid&gt; does not exist"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by malajand on 2009-12-09
Hello,

i have both windows and ubuntu installed on my computer. It has been ok till some days before. Now i cant open neither windows or ubuntu. When i try to open ubuntu with the first kernel 2.6.27-15-generic i get the computer blocked. If i try to open the old kernel 2.6.27-7-generic  i get the message

_/dev/disk/by-uuid/..(numbers: i think is the UUId adress)..  does not exist_

If i try access with a live cd to get my files i get the message

_kernel panic not syncing No init found. Try passing init=option to kernel_

or

_kernel panic not syncing VFS: unable to mount root fs on unknown block (8.1)_


Have you any idea to solve this?

Thank you for attention

---

### Post by phillw on 2009-12-09
> **malajand said:**
> Hello,

i have both windows and ubuntu installed on my computer. It has been ok till some days before. Now i cant open neither windows or ubuntu. When i try to open ubuntu with the first kernel 2.6.27-15-generic i get the computer blocked. If i try to open the old kernel 2.6.27-7-generic  i get the message

_/dev/disk/by-uuid/..(numbers: i think is the UUId adress)..  does not exist_

If i try access with a live cd to get my files i get the message

_kernel panic not syncing No init found. Try passing init=option to kernel_

or

_kernel panic not syncing VFS: unable to mount root fs on unknown block (8.1)_


Have you any idea to solve this?

Thank you for attention


Hi,

Re-installing Grub2 and correcting UUID's is covered here --> [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I know, been there, got the Tee-Shirt - lol

Regards,

Phill.

---

### Post by malajand on 2009-12-09
i cannot boot from live cd. I get kernel panic..... How can i solve from busybox or grub command line?

Thank you

---

