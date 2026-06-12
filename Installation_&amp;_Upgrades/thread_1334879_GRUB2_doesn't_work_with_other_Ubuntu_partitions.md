---
title: "GRUB2 doesn't work with other Ubuntu partitions"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2009-11-22
Decided to take the plunge and install Karmic this weekend.

Have done clean installs like this for years, and there's always something that doesn't work.  In this case, it appears to be the new GRUB.

Setup is as follows:
-- Disk 1: Ubuntu 9.10 (boot disk) (sda)
-- Disk 2: Ubuntu 9.04  (sdb)
-- Disk 3: Windows 7 & Vista (sdc)

Disconnected disks 2 & 3, installed Karmic to disk 1.  Booted -- OK.

Hooked up disks 2 & 3.  Rebooted, selected Karmic -- booted OK.  Ran update-grub.  Found other Ubuntu (9.04) and MS Windows OS's.  
However, during update-grub, got the error message "can not find a GRUB drive for dev/sdb1  check your device.map"

Rebooted.

Selecting 9.04 yields error message "error: you need to load the kernel first, press any key to continue".  Pressing a key returns the GRUB menu.

Selecting MS Windows entries work fine.  (sure surprised me! This has always been the hard work in the past)

Back in the "good old days" (last week), I would have hand-edited the menu.lst file and had this fixed in about 10 minutes tops.  But now, we're not supposed to be hand-editing anything in the new GRUB setup.

So, given that I CAN boot into Karmic OK, once there, (1) what can I do to track down this error and (2) how can I fix this?

---

### Post by presence1960 on 2009-11-22
I know this will sound dumb- but i had similar problems. Even though GRUB2 was installed with my clean install, I installed it again from Syanptic (grub-pc) and it fixed the problem. I am now able to boot 9.04 and XP. Initially after the clean install they would not boot. Do not ask me why because I have no idea.

---

### Post by oldfred on 2009-11-23
What does you device.map look like (in boot/grub). Your initial install only had sda, but now you have added 2 more drives.

I have seen this command and I think it rewrites device.map and maybe some other things.

sudo dpkg-reconfigure grub-pc

edit more info from this bug discussion:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420077](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420077)

Also, as a general rule, please make sure that you've run grub-install
on the right devices since the last upgrade. Run this command to see
what's done automatically:
   sudo debconf-show grub-pc | grep install_devices
 If this doesn't match the drive(s) you're booting GRUB from, then you
need to run 'sudo dpkg-reconfigure grub-pc' to change it.

---

### Post by Mark Phelps on 2009-11-23
Hey guys ... many thanks for the quick responses.  

I'll be sure to check these out.

---

### Post by Mark Phelps on 2009-11-23
Added two lines to device.map, ran update-grub, now everything works!

That was just way too easy! (sort of takes all the fun out of it)

But anyway ... thanks a lot guys.

---

