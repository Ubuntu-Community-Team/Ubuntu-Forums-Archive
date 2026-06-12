---
title: "Testing out upgrades by using unionfs"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by eschvoca on 2008-11-11
Hi,

I want to install Ubuntu 8.10 in a way that I can revert back to my old installation without using a lot of disk space.  Currently I use 3 partitions:

/sda1 -> /          # root1 (previous Ubuntu version)
/sda2 -> /mnt/sda2  # root2 (next Ubuntu version = 8.10)
/sda3 -> /home      # home

Usually when I upgrade I re-use my old home directory and do a fresh install into the other root.  If the install works out poorly I switch back to the old root and most things are good except that my home directory has been upgraded to the newer Ubuntu and when I go back to the older version I may run into problems.  (And yes I do a backup before the process to help me downgrade it back but the process is not optimal.)

So my new hope is to use unionfs on /home so I can make my Ubuntu 8.04 read-only and put a unionfs mount on top.  I don't know if Ubuntu 8.10 can do this on the install (or how to do it).  Also, if the upgrade goes successful I want to make my /home read-write and merge my unionfs layer back into it and then no longer use unionfs.

Does anyone have instructions on how to do this?  Is there a better way to achieve the same thing (without using lots of extra disk space for /home?  

Thanks,

.e

---

