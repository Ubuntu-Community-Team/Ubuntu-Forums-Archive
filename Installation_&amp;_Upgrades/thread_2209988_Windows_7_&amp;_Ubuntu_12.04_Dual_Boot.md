---
title: "Windows 7 &amp; Ubuntu 12.04 Dual Boot"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by mike156 on 2014-03-08
Hey everyone,

I have a Dell Inspiron and decided to make it a dual boot between Windows 7 Professional x64 and Ubuntu 12.04 LTS x64.
My HDD has 500gb and partitioned this way:
- System Reserved NTFS 100mbps (Windows boot)
- Partition C NTFS (75GB, Windows itself)
- Partition D NTFS (some documents of mine)
- Partition E NTFS (120GB, other stuffs)
- Partition F NTFS (50GB, work related)
- partition 1GB (ubuntu boot)
- partition 15GB (ubuntu root)
- partition 50GB (ubuntu home)
- partition 4GB (ubuntu swap)

Installed Windows first and Ubuntu after, and now i want to make a selection screen so I can choose what system to boot at startup (Don't even think about saying EasyBCD).

However, I am trying to make the OS Selection screen and thought of 2 choices:
1. Use GRUB (how do i link grub to be the first) 
2. Use Windows to ask which OS i want to load? (again, how do i do that?)

Thanks

---

### Post by raja.genupula on 2014-03-08
Hmm Ubuntu can automate it for you. All you have to do is simply choose install alongwith Windows.
Thats do Ubuntu install with no damage to your Windows install and then from GRUB screen you can choose what OS you want to boot.

If its not exactly what you want then be more clarify at your post.

---

### Post by mike156 on 2014-03-08
I want that the boot loader of Windows and Ubuntu's to be stored in different partitions so I can reinstall each one of them without any problems after.
Selecting alongside install, will i still be able to select which and what partitions I want to use for Ubuntu?

Also, how do I remove generic kernel and memtest from Grub Menu?

---

### Post by raja.genupula on 2014-03-08
1. You can choose where you want to install Ubuntu & from Grub screen you can choose what you want to boot.
2. By using Grub_customizer you can choose what options you would like to see in GRUB screen.

Hope that helps.

---

### Post by mike156 on 2014-03-08
Thanks a lot, worked and runs smoothly :D

---

### Post by Mark Phelps on 2014-03-08
> and just to save time and not opening a new thread.

Your new topic is totally unrelated to the topic of this thread -- please open a new thread.

---

### Post by mike156 on 2014-03-09
Well, just noticed...installing alongside windows puts ubuntu in one partition...i want to use all 4 partitions that i created for ubuntu...any other ideea?

---

### Post by oldfred on 2014-03-09
You choose partitions to use when using Something else on partitioning screen. You choose which partition, its format and mount point.
Most desktops do not need a separate /boot. Servers, RAID or LVM may need a /boot.

---

