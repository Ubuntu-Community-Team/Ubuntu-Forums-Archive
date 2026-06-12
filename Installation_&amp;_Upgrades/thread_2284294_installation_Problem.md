---
title: "installation Problem"
date: 2015-06-28
forum: Installation &amp; Upgrades
---

### Post by Amal_Madawa on 2015-06-28
Hi i'm using windows 7 with 6 partitions. I want to install Ubuntu with windows 7. is there is any problem, when Install Ubuntu with 6 partitions ? if there is any problem what will happen to the data ?

Amal

---

### Post by dino99 on 2015-06-28
if your hardware is drived by uefi, then there is no partition limitation; otherwise with a bios, the 'primary' partitions are limited to 4.
you can glance at the many threads/answers posted by 'oldfred' to get all the explanations (and more)

---

### Post by yancek on 2015-06-28
The fact that you have 6 partitions will not make any difference.  You will need free/unallocated space on which to install Ubuntu as you won't be able to install to a windows filesystem.  Might be a good idea to view a tutorial on dual-boot such as the one at the link below especially important if the process is new to you:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Amal_Madawa on 2015-06-28
> **dino99 said:**
> the 'primary' partitions are limited to 4.

 4 partitions are "logical"

---

### Post by ajgreeny on 2015-06-28
It could help people if you can show us a screenshot of the partitions as seen by gparted, which is available by default in all the live systems of *ubuntu.

That will show us how the current partitions are laid out on the disk and which are most likely to be best to shrink to make space for Ubuntu.  Unlike Windows, which will not boot from a logical partition, Linux and Ubuntu is not so fussy, so you can make all your Ubuntu partitions as logical ones.

---

### Post by Amal_Madawa on 2015-06-29
<img src="http://ubuntuforums.org/attachment.php?attachmentid=262924&amp;stc=1" attachmentid="262924" alt="" id="vbattach_262924" class="previewthumb">

---

### Post by ajgreeny on 2015-06-29
No, sorry but I need a gparted screenshot as the windows disk-management screenshot is useless for linux partitions.

---

