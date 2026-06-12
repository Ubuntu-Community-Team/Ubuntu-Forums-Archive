---
title: "Unable to find boot drive"
date: 2022-05-26
forum: Installation &amp; Upgrades
---

### Post by morenocr on 2022-05-26
So some background on what could be the problem is I dual boot a lot of linux distros and then want to dual boot a windows operating system on top of it. After that my laptop is getting some weird glitches that makes doing basic task on it basically impossible. So then I tried to remove all of the drive using gprated-live included the EFI partition that after doing some research is not good to get deleted. After that nothing works getting some firmware bug messages, kernel panic, etc. 

boot-repair log: [https://paste.ubuntu.com/p/T4T2Xk2KxH/](https://paste.ubuntu.com/p/T4T2Xk2KxH/)

---

### Post by yancek on 2022-05-26
The boot repair output shows you have an EFI install of Ubuntu which is on sda2.  You have an EFI partition (sda1) but it does not have any of the necessary boot files.  Have you tried the option of reinstalling Grub EFI suggested in boot repair?

---

