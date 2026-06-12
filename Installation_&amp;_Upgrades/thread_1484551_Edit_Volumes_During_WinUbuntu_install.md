---
title: "Edit Volumes During Win/Ubuntu install"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by mcarrigan on 2010-05-15
Ok, I am doing my first install on my new Dell laptop so I can make the change from Win7 to Ubuntu.  Right now I don't want to fully dump Win7 so I want a duel boot. During the install it finds windows and asks if I want to do a side by side.  In the past I have always manually edited the vols myself but it has been a few years since I have done this plus Dell has other partitions already out there.  This is what I have right now:

/dev/sda1 - fat16 - 41MB
/dev/sda2 - ntfs - 15728 MB
/dev/sda3 - ntfs - 484337 MB

My goal is to have Win7 in a 100GB vol, Ubuntu in a 100GB vol then the remains in its own vol, this is where I will store all my stuff to make it easy if I need to access no matter which system I'm in.

So, what are the steps to break the sda3 up so i do it right? (if there are already steps out there, my bad, short on time to search, just point me to the link)  also, if I can drop each OS vol down in size without causing problems, how low can I go?

Thanks a bunch!

---

### Post by darkod on 2010-05-16
Boot win7 and go into Disk Management (either trough Control panel or the command to search for is diskmgmt.msc).

Use it to resize your system partition to 100GB. Is that /dev/sda3? Once it's resized leave the space created as unallocated.
Reboot win7 few times because it will want to do some disk checks.
After that start the ubuntu installer and use Manual Partitioning to set it up, either with separate /home partition or not, as you wish. You will need to create a minimum / and swap partitions. A separate /home is your choice. If you need more advice about these steps, just ask. Since you've done partitioning earlier, the process is very straight forward.

Because you already have 3 primary partition you will have to create the ubuntu partitions as logical, which is no problem.

After ubuntu is installed, create the remaining space as ntfs which you can do from either win7 or ubuntu, shouldn't matter.

---

