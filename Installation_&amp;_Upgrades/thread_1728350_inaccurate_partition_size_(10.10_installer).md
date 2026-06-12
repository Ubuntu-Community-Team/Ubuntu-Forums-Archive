---
title: "inaccurate partition size (10.10 installer)"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by groogrux on 2011-04-13
Hello, I am dual-booting Windows 7 and Ubuntu 10.10 (32 bit) and I used Windows to shrink the C drive, to allow space for Ubuntu. I used a LiveCD to install Ubuntu with the "alongside other operating system" option.  I did not move the slider, leaving it around 75% Windows, and 25% Ubuntu.  After the install, the partitions were more like 60% Ubuntu, and 40% Windows.  I corrected it with GParted, but I was wondering why this happened.  Could anyone let me know?  Thanks.

---

### Post by Dutch70 on 2011-04-13
It's not advisable to use the "alongside other OS" function with version 10.10 at all. If it didn't really mess windows up, consider yourself very lucky.

---

### Post by Hedgehog1 on 2011-04-14
This happened because you shrank windows manually (a good thing) and did not create the Ubuntu partitions manually and the select this option:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

And then assign those partitions you created:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]



***The Hedge***

:KS

---

### Post by groogrux on 2011-04-14
That makes sense.  Thanks for the quick responses!  I was a little worried about specifying the partitions manually in Ubuntu, because I was really new to it at the time.  Now that I can make more sense of / and swap, I'll probably do next time.

---

