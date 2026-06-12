---
title: "Need help, first time instaling second os"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by ComradeScapes on 2009-12-08
Hi, i currently have windows 7 and im looking to install ubuntu on my computer along side with my windows 7, i have never had 2 os on the same computer before so im not sure how to do this, iv'e tried looking on the internet for guides but they aren't that helpful, i only have 1 partition which is my whole hard drive, is it possible for me to create a second partition without have to reformat it? or at this point now, do i have to just start from scratch?

---

### Post by MelDJ on 2009-12-08
ubuntu studio uses the text based installer. hence, when you come to the partition editor(i believe its called that), you will have to select manual to manually set the partitions.
this is way harder than install a normal ubuntu through the live cd ;)

---

### Post by ubhi on 2009-12-08
step by step graphical instruction for dual boot with vista & ubuntu.


[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by hardfire_avk on 2009-12-08
ok! here you go, 
you can actually shrink a partition in windows 7 and create two different partitions without losing your data
for informatino on shrinking see this link [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

and then , reboot the system with ubuntu CD , then follow the steps.
The most important part is the partitioning , when you have to select the new partition, not the one that you have windows 7 in.

Hope that's clear.

---

### Post by ComradeScapes on 2009-12-08
Thank you all, im in the middle of resizing right now actually, this has probably saved me a lot of stress of reformatting haha, and i have 2 very different sizes so i will know which one has windows 7 on it, again thank you for alll your help

---

### Post by darkod on 2009-12-08
> **hardfire_avk said:**
> ok! here you go, 
you can actually shrink a partition in windows 7 and create two different partitions without losing your data
for informatino on shrinking see this link [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

and then , reboot the system with ubuntu CD , then follow the steps.
The most important part is the partitioning , when you have to select the new partition, not the one that you have windows 7 in.

Hope that's clear.
 
Just to add, do only the resizing in win7. Leave the space that will be created as unallocated. Do NOT create any partition planned for linux in windows, it can't create the needed filesystem. NEVER. You only get in trouble when installing ubuntu later because it will consider the partition as unusable space. You would have to delete it again which is additional work and can be confusing especially if new to the install process.

---

