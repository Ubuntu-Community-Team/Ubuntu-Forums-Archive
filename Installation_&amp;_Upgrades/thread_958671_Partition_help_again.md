---
title: "Partition help again"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by adamant715 on 2008-10-25
Ok, I'm currently running on the LiveCD  right now and I'm wondering what Partition to choose, cause I want to dual boot WinXP and Ubuntu on seperate Partitions. Heres my options.

---

### Post by adamant715 on 2008-10-25
I also want to note on Windows theres a Partition that is 100& free and has 15.7GB but in ubuntu it says that I used all of it...

---

### Post by bulldog on 2008-10-25
You didn't install ubuntu yet?
Windows will see your ext3 [ubuntu] partition as an empty partition because it can't read ext3 by default.
If you want to install ubuntu,you'll have to choose sda1 for the install.
Be sure your windows is on a primary partition,otherwise it won't boot anymore,ubuntu can be installed on an logical partition.

I recommend to make three partitions at least for your ubuntu.
A 10GB for /  [system]
A 1-2GB for swap
The rest of the free space for /home
This can all be logical partitions within an extended partition,ubuntu doesn't matter.
As long as windows is on a primary partition you're safe.

---

### Post by Pumalite on 2008-10-25
Get Gparted Live CD and 'shrink' XP, then install in the new space. Defrag several times after turning PageFile to '0'; then use Gparted:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. (it works with unmounted drives/partitions)

---

