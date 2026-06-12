---
title: "want to install xubuntu on 1st partition, xp in the 2nd"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by AlmaMater on 2006-08-31
hi all

i know that normally, once install win Xp on first partition and then in the second partition linux,

is because if u install win XP after, it will mess whit the grub??

if so??  any chances i can fix it

coz i want to have installed Xubuntu on my first partition, and win XP on my second (1 single HDD)

any advice on how can i repair the loader after win xp destroy all my first partition after installation? : p

thanks

---

### Post by grimmson on 2006-09-01
To restore grub try [http://www.ubuntuforums.org/archive/index.php/t-24113.html](http://www.ubuntuforums.org/archive/index.php/t-24113.html) second message down. 
That wont work if xp really destroyed the first partition. If xp formated or installed over your first partition its gone. If xp just replaced the grub that should work. You may create a xp restore disk or [https://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](https://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/) first. sounds like things are buggy, make sure you understand whats happening please.

---

### Post by luvr on 2006-09-01
If you make sure that the first partition is formatted as a Linux system, then Windows XP won't touch it. You can, then, install Windows XP in the second partition.

Even in this scenario, you can install Windows XP (in the second partition) *first* and Linux (in the first partition) *second.* (I have already done so more than once. **Do** make sure that the first partition is formatted as a Linux filesystem *before* you install Windows XP, though.)

If you have already installed Linux, then Windows XP will overwrite the GRUB boot loader when you install it next. See the earlier reply from **grimmson** on how to restore GRUB.

---

