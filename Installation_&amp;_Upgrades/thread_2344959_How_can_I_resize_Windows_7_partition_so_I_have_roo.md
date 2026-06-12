---
title: "How can I resize Windows 7 partition so I have room to install Ubuntu?"
date: 2016-11-29
forum: Installation &amp; Upgrades
---

### Post by yodayams on 2016-11-29
I just got a new laptop (Acer) and it comes with Windows 7 installed on the whole hard disk. I need to shrink the Windows partition and make room so I can install Ubuntu. I want to dual boot Windows and Ubuntu. Please tell me exactly what I must do. Thanks.

Zach

---

### Post by slickymaster on 2016-11-29
Hi yodayams, welcome to the forums.

In the Disk Management screen, just right-click on the partition that you want to shrink, and select &#8220;Shrink Volume&#8221; from the menu. In the Shrink dialog, enter the amount you want to shrink by, not the new size. Don't forget to defragment the partition before resizing it.

---

### Post by yodayams on 2016-11-29
Thanks so much, that worked great! Will the Ubuntu installer detect that i have Windows and setup grub for dual boot or must I configure grub manually?

---

### Post by slickymaster on 2016-11-29
The Ubuntu installer will detect your windows 7 installation.

Before doing anything I'd recommend you to have a read at the [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot?action=fullsearch&value=linkto%3A%22WindowsDualBoot%22&context=180") wiki.

---

### Post by yodayams on 2016-11-29
Ok great! I will read it now. Thanks!

---

