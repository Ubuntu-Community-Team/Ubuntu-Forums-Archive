---
title: "From dual to tri-boot partitiioning question"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by Oldude on 2007-12-13
Advice please.  My system is dual boot with Windows XP and Ubuntu 6.06.  I have a DVD for 7.10 to install.  I want to keep the 6.06 in place until 7.10 is up and running.  There is lots of  hard drive space available.   6.06 is set up with 3 partitions- root, swap and home.  
My questions- Can I leave the swap and home partitions alone and create a new root for 7.10?  If  root is designated with a / for 6.06, then do I use /2 for the 7.10 root partition? 
I have exceeded my point of ignorance and am now in need of expert advice.  Thank you all.

---

### Post by Pumalite on 2007-12-13
In this new space you have, use Gparted Live CD and create a 10 GB partition for '/' and the rest for /home; both for 7.10. The old /swap is all you need for both.

---

### Post by Oldude on 2007-12-13
OK, that's good info.  Thank you for the reply.  I'll give it a shot tomorrow  morning.

---

### Post by Pumalite on 2007-12-13
You are welcome. Good luck.

---

