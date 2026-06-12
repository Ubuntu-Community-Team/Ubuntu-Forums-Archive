---
title: "Cannot format hard drive"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by fight2survive on 2010-12-23
I am trying to install ubuntu on a seperate hard drive than the one i have windows 7 installed on. i have two 500 gb hard drives in my computer; one i only want to use for windows, and the other only for linux.

The hard drive that i am not using yet (the linux one), for some reason, has a 100mb "system restore" partition on it, which i do not want on there...but when i try to format the drive in gparted, it says "cannot format drive, daemon inhibited"...i also tried in fedora 14's disk utility, same error and message, and in windows partitioning utility, it tells me it cannot format this drive.

Need help with this, thanks!

---

### Post by Lone_Joker on 2010-12-23
Are you sure that partition is not mounted? Partitions must be unmounted if you want to partition them.

Basically, if you can see the partition under "Places" when you're using a Live CD (that's what you're using right?) then it is mounted and you have to unmount it.

---

### Post by pbpersson on 2010-12-23
When you boot over to Windows 7, is this hard drive that is giving you the trouble a basic drive or dynamic drive?

I Googled your error message and saw some articles stating you will need to revert this back to a basic drive before you can proceed.

---

### Post by ottosykora on 2010-12-23
i would also make sure that you do  not need this partition, since this might be essential part if your w7 goes into problems.
How did the partition in question came to that drive?

---

