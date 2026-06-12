---
title: "Uninstall Ubuntu 10.10 in dual boot just with formatting with LiveCD?"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by The Wish Within on 2011-01-03
Hi.
I have Ubuntu 10.10 and Win7 in dual boot on my Asus EeePC T101MT.
However, it's a touchscreen netbook and in this case, Win7 is much better for me. I have no use for Ubuntu.
Now I want to uninstall it.
Now the question is: 
Can I simply format all Linux partitions with the LiveCD to uninstall it without having booting troubles for example because of GRUB afterwards?

---

### Post by dino99 on 2011-01-03
grub is installed into the mbr not into ubuntu partitions, so you need to remove grub first, then reboot into w7 then format the ubuntu patitions

---

### Post by The Wish Within on 2011-01-03
How can I remove GRUB from mbr?
//Edit: I've read you could do this with a windows CD but the only CD I have is a recovery CD...
What should I do?

---

### Post by mikewhatever on 2011-01-03
Check out the howto below.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
There is a link to download a W7 repair cd.

---

