---
title: "Removing windows from a ubuntu/vista dual boot?"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by GIAA on 2010-03-29
I currently have vista and Ubuntu 9.10 on my computer as dual boot and have a virus on windows that made it impossible to even log into windows so I want to remove it from the computer as it's just wasted space and just use ubuntu. 

I have found plenty of info for going the opposite way but not much on going to linux only...

I know how to delete the partition with GParted but not how to reclaim the space. Any help would be greatly appreciated

---

### Post by oldfred on 2010-03-29
The easy way is just reformat the partition with gparted and use it as a data partition. If you expand the adjacent partition it will be very slow as it has to move all the data and if it is your install, moving the start in some cases can cause problems. It is always easier to add space to the end of an existing partition but not the beginning.

---

### Post by GIAA on 2010-03-29
Thanks for the reply
I haven't got much experience with GParted though and just noticed that vista is in there as sd2 and has boot next to it... is there something I should do before I start screwing around with it?

---

### Post by oldfred on 2010-03-29
Linux does not need a boot flag, but some BIOS want to see a boot flag to let the system boot. I would move the boot flag and just use gparted to reformat the partition. 

Then you will want to know about mounting and fstab to permanently mount the partiiton.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by GIAA on 2010-05-15
Thanks for all the info haven't had a chance to read through it yet and try and figure it out but I will post and say what the outcome is when I do

---

### Post by wilee-nilee on 2010-05-15
> **GIAA said:**
> Thanks for all the info haven't had a chance to read through it yet and try and figure it out but I will post and say what the outcome is when I do

Just so you know there are bootable AV iso's and hirens you can clean up the Vista, but it may be to destroyed to run correctly in the end.

---

