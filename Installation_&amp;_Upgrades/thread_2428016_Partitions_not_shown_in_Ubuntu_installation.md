---
title: "Partitions not shown in Ubuntu installation"
date: 2019-09-28
forum: Installation &amp; Upgrades
---

### Post by r-shift123 on 2019-09-28
I'm trying to install Ubuntu dual boot with Windows 10 already installed. However, during installation, none of the partitions I made are shown.
I've tried using chkdsk but it didn't help. 
I'm using a Dell XPS 15. 
I added screenshots below.

---

### Post by wildmanne39 on 2019-09-28
Hello and welcome to the forum.

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by r-shift123 on 2019-09-29
[ATTACH=CONFIG]284099[/ATTACH][ATTACH=CONFIG]284100[/ATTACH]

---

### Post by r-shift123 on 2019-09-29
My bad. Just changed it. Thanks.

---

### Post by yancek on 2019-09-29
One common reason for this is that windows is in its default state which is hibernated.  You should turn off fastboot and anything related to hibernation on windows so that Ubuntu will mount and show the windows partitions.   Dual booting with windows 10 on an EFI system which you seem to have is explained at the Ubuntu site below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

