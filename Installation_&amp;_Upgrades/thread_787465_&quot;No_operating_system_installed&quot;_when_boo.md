---
title: "&quot;No operating system installed&quot; when booting from external hard drive"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by matthewbpt on 2008-05-08
Hello all,
This is the first time I've installed Ubuntu or any kind of linux. I just tried to install it from my laptop on my external hard drive, Western Digital 500gb. Now when I try to boot from the external hard drive it gives me the message "No operating system installed" and will not boot into Ubuntu. I installed it from the LiveCD (Ubuntu 8.04) on a 15gb partition on it and installed the GRUB bootloader also onto that partition. What am I doing wrong?
I can boot into Vista (which I am using now) from my internal hard drive fine, but not into ubuntu from my external.
My laptop has the following specs:
AMD Turion64 TL60 (2.0Ghz dual core)
2048mb RAM
Geforce go 7600 with 344mb dedicated memory

---

### Post by matthewbpt on 2008-05-09
Ok i reinstalled it on the 15gb partition and now it does load the GRUB bootloader menu, but when I try to boot into ubuntu it says "error 17".
How can I fix this? =(

---

### Post by TryMe on 2008-05-09
Unfortunately what you want to do is not the simplest thing. Yet, it can be done with some trial and error. 
check out this thread: [http://ubuntuforums.org/showthread.php?t=80811]("http://ubuntuforums.org/showthread.php?t=80811")

I hope that helps.

---

### Post by matthewbpt on 2008-05-10
Thank you. I managed to fix the problem, had to change the boot menu because it had the wrong drives for linux, (hd1,1) instead of  (hd0,1). Had to first press "e" in GRUB to edit where to boot from temporarily and them use the terminal when it booted intu Ubuntu to change it permanantly.

---

### Post by Johnsie on 2008-05-10
I'm glad you got it working... Obviously you have good IT skill which helped. However I cant see the see the average joe or granny being able to do this so maybe it's something canonical should look at improving.

---

