---
title: "I have a problem with partitioning  my hard disk. What should I do?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by FastMady123 on 2008-01-06
I did a 5GB ex3, I did a 1GB linux-swap and, I try to do the rest of the hard disk. I got a error message saying I can only have four partitions on my hard disk. I need to have three. What should I do?

---

### Post by yabbadabbadont on 2008-01-06
Remove those two, then create one extended partition.  Then create the others as logical partitions, within the extended.  That gets you around the four primary partition limit.

Edit: The extended partition should be as big as the total size of all of your linux partitions together.  (since it will hold all of them)

---

### Post by confused57 on 2008-01-06
You can only have 4 primary partitions per hard disk, however one of these can be an extended partition containing many logical partitions:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

Ubuntu can be installed on logical partitions, with no problem...

---

