---
title: "grub rename after kernel upgrade"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by daschmidty on 2007-04-14
I am running the latest fully upgraded version of kubuntu feisty, and on odd thing happened yesterday when i upgraded to the newest kernel image(20-15). When I booted my system, GRUB has renamed all of the entries for "Ubuntu kernel ..." to "Debian GNU/Linux kernel ...". While it is not a major issue and i know it can be corrected by editing menu.lst, I was just wondering if anyone else has had this issue, and what might be causing it.

---

### Post by Malac on 2007-04-14
> **daschmidty said:**
> I am running the latest fully upgraded version of kubuntu feisty, and on odd thing happened yesterday when i upgraded to the newest kernel image(20-15). When I booted my system, GRUB has renamed all of the entries for "Ubuntu kernel ..." to "Debian GNU/Linux kernel ...". While it is not a major issue and i know it can be corrected by editing menu.lst, I was just wondering if anyone else has had this issue, and what might be causing it.
Open /usr/sbin/update-grub in kate and find the section:
```
# Title
title="Debian GNU/Linux"
```
and change it to :
```
# Title
title="Ubuntu"
```
Suspect the dev's missed it.

---

### Post by daschmidty on 2007-04-14
Thanks, worked perfectly! Though my update-grub was in /sbin instead of /usr/sbin.

---

