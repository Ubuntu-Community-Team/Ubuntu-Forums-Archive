---
title: "Need help in installation"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by shapira.alon on 2007-05-09
Hi, I downloaded the  ubuntu-6.06.1-desktop-i386.iso  file and run the md5sum check (passed ok).
Then I burned it on a cd, but it does not work.
When I choose the 'Check CD for defects'  (after booting from the cd) it get stuck just
in the beginning of the check and then reports:
(start qoute)
Uncompressing Linux... OK, booting the Kernel.
[17179572.884000] PCI: Failed to allocate mem resource #6:20000@90000000 for 000
0:01:00.0
(end quote)

Any one knows what I've done wrong ?

---

### Post by Stormspireiv on 2007-05-09
Try this to see if your iso download is OK. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, an error might have occured while burning the iso to a CD. You may want to try re-burning it.

---

### Post by Stormspireiv on 2007-05-09
(sorry for double post) 
I didn't catch that you already ran the hash check. As I said earlier, try re-burning it to a new CD and don't use an RW if at all possible.

---

### Post by confused57 on 2007-05-09
Here's how to burn an Ubuntu iso(or any iso, for that matter):
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

make sure to select burn as an "image", not a data or bootable cd...burn at a slow speed(8x or less)

---

### Post by shapira.alon on 2007-05-09
Thanks for your help.
It turns out that there is a different problem, the disk works
just fine with my old pentium 4 computer.

---

