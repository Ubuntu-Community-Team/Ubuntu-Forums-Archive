---
title: "Failed to unmount partitions"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Ohbie on 2008-02-17
Hello all,

I'm trying to install Ubuntu and using GParted I have already partitioned my /dev/sda1 to create an unallocated 10GB partition which I plan on installing Ubuntu onto because I want to be able to dual boot Windows XP.  Using the installer I chose the "Guided - use the largest continuous free space" option.  Selected to import my account from Windows XP and then created my account.  Once I get to the end I click the Install button.  Then the installing system load bar gets to 15% - Detecting file systems... and then I get an error message which reads,

[INDENT]Failed to unmount partitions

The installer needs to commit changes to partition tables, but cannot do so becasue partitions on the following mount points could not be unmounted:

/media/disk

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?[/INDENT]

Now I'm very new at using Ubuntu as well as partitioning drives and such so I'm not exactly sure what the problem is here.  Any knowledgeable advice would be greatly appreciated.

I am also installing this on a Dell Inspiron E1705 if that helps.

Thanks for your help.

---

### Post by dstew on 2008-02-17
That mount point is probably used by the installer to get your account information from WIndows, and for some reason it could not unmount the partition. That is, the routine that copies your account information either was not finished at the time, or got hung.

I would recommend doing the installation again, but skip the "import Accounts" step. Maybe it will work better that way.

---

### Post by Ohbie on 2008-02-18
I tried that, but to no avail so then I just shut down the computer.  Went back into windows and did some work.  I figured I'd try it again and so I restarted from the Ubuntu CD and the installation went perfectly.  Thanks so much dstew.

---

