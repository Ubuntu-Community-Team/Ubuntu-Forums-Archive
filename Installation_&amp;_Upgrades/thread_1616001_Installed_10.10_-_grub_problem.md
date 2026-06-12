---
title: "Installed 10.10 - grub problem"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by johan.dho on 2010-11-07
I installed Ubuntu 10.10 in /dev/sdc5, and the corresponding boot also in /dev/sdc5. 

(*) I have several os on my pc, and my main boot program is LILO. I always install 
the OS, and it's MBR on the same partition .


Everything is installed, eg, I can see the whole file system on /dev/sdc5, but I can't
boot into it. 


* When i add the other=/dev/sdc5 to lilo (from another OS, another partition), I get 
  "not a valid boot sector" warning. 

* When i boot, the computer hangs


Any ideas as to how to continue would be appreciated.

---

