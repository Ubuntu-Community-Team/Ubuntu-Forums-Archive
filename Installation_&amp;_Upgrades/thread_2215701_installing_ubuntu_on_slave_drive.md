---
title: "installing ubuntu on slave drive"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by infyniti on 2014-04-07
I have two hard drives, on c i have windows and would like to install ubuntu on the slave drive. after selecting the salve dirve, i am getting "no root file system is defined". I tried deleting all partitions on the slave dirve too. I am attaching couple of screen shots, can any one please suggest what i am doing wrong. 
Thanks
Anant

---

### Post by oldfred on 2014-04-07
Your thread already says Solved. Not sure if then others may also see thread.

If you use Something Else you have to manually create partitions with + to add partition. Or you can partition in advance and then use Something Else to assign which partition is which with change button.

With two drives it is better to use Something Else as you also can see at bottom of screen shot the combo box to change to load boot loader to sdb. It looks like you have done that.

The default install is just / (root) and swap. And if a new user that is all you need. And if it is only 40GB that is all your should need. Swap can be equal to RAM in GiB not GB or a bit larger than RAM otherwise. If you have lots of RAM or 4GB or more then swap can be just 2GB as system may never use swap unless you hibernate.

---

