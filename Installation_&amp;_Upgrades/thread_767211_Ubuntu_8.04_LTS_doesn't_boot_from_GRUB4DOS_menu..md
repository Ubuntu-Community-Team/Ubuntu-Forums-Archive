---
title: "Ubuntu 8.04 LTS doesn't boot from GRUB4DOS menu."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by danflasher on 2008-04-25
Hi;

I just install Ubuntu 8.04 LTS (HARDY HERON) on a laptop running XP Professional. When the system reboots, I see the GRUB4DOS dual boot menu asking me if I want to boot XP or Ubuntu. Every time I select Ubuntu, the GRUB4DOS dual boot menu gets displayed again and Ubuntu never starts up.
Does anyone know why I can't get Ubuntu to start from the GRUB4DOS menu?

Thanks
Dan

---

### Post by tormod on 2008-04-25
It would be easier if you could attach your menu.lst here (rename it to .txt to outsmart the forum software). On which partition did you install Ubuntu?

---

### Post by danflasher on 2008-04-26
Ubuntu was installed in the C:\ partition. I didn't know where to find (menu.lst) so I performed a search. I found three locations where menu.lst exists. I noticed the file which exists in the grub path has a size of 3KB whereas the size of the file in the C:\ path has a size of 1KB. Is it possible the menu.lst file isn't getting copied to C:\?
I attached the 3KB menu file.

[FONT="Times New Roman"][FONT="Courier New"][SIZE="2"]Name                In Folder                              Size      Type      Date Modified
menu.lst            C:\                                      1 KB    LST File     4/10/2008  8:19 PM
menu.lst.bak      C:\                                      1 KB    BAK File     4/10/2008  8:17 PM
menu.lst            C:\ubuntu\winboot                1 KB    LST File     4/22/2008  8:57 AM
menu.lst            C:\ubuntu\install\boot\grub    3 KB    LST File    4/25/2008  10:15 AM [/SIZE][/FONT][/FONT]

Thanks
Dan

---

### Post by tormod on 2008-04-26
It seems like you used WUBI to install Ubuntu in a windows partition? This is useful information you could give from the beginning ;) The file you attached was only used during installation I think. grub4dos uses the one on C:\ Can you please attach that one?

---

### Post by danflasher on 2008-04-26
I attached the menu.txt file located in the C:\ directory.
Sorry about leaving out part of the story.

Dan

---

