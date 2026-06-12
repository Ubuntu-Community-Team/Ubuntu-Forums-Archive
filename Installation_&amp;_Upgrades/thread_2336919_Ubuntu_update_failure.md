---
title: "Ubuntu update failure"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by hudini on 2016-09-12
I have the same problem and when I ran 'df' I got

```

root@ubuntu:/# df
df: no file systems processed
```

---

### Post by QIII on 2016-09-12
Moved to its own post from [https://ubuntuforums.org/showthread.php?t=2335584](https://ubuntuforums.org/showthread.php?t=2335584).

While it may seem that you have the same issue, you may not.  Please allow the OP of the other thread to get personal attention to their issue and we will be sure that you get personal attention to yours.

Thanks.

Cheers!

---

### Post by ian-weisser on 2016-09-12
1) Exit from root and try 'df' as a normal user. Same result? Or different?

2) Try 'du /tmp'. Same result? Or different?

There's an old bug in df that occurs when using su to gain root.
If both df and du fail, then your disk is probably 100% full.

---

### Post by hudini on 2016-09-13
Thanks for the quick reply! I ended up fixing my original issue causing the errors on **sudo apt-get install -f **and **sudo dpkg --configure -a**. I had encountered a kernel panic on boot after an interrupted upgrade from 14.04 to 16.04. Had to use a live cd to try to finish the update but the apt-get install and dpkg weren't working. I can't remember exactly what I tried (I'm not super proficient with linux and was reading and trying a ton of stuff) but I think it was using **apt full-upgrade** to get the packages in order and following this recovery guide [https://ubuntuforums.org/showthread.php?t=1920317](https://ubuntuforums.org/showthread.php?t=1920317).

My original error happen to be the same as the OP from [https://ubuntuforums.org/showthread.php?t=2335584](https://ubuntuforums.org/showthread.php?t=2335584) so I thought it might be related.

---

