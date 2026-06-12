---
title: "Error after fresh install"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by Al_Hennessey on 2014-11-12
Hi. I am trying to install the latest Ubuntu. When the installation finished it restarted and gave the error "Failure reading sector 0x4f4808 from hd0". I am not sure why this is happening. It does this every time on restart. I managed to get to the terminal not sure how but I inserted the live CD and I ran boot-repair and it gave the this URL

Paste.Ubuntu.com/8972967

However it still won't boot without cd .
Just a bit of background I originally installed windows 7 alongside Ubuntu. However I had enough of windows and decided to try to wipe everything and just install Ubuntu. This worked, however for one reason or another I tried to reinstall Ubuntu again and this is where I am getting the errors. Not sure why this is happening as it was working before.
Thanks for any and all help.

---

### Post by ubfan1 on 2014-11-12
Sounds like a bad block.  From the live media, run sudo mke2fs -c -c (on wherever you mount the partition) to remake the filesystem skipping bad blocks.  Then reinstall and see it that helps.  Thats twice on the -c to force a write/read check.

---

