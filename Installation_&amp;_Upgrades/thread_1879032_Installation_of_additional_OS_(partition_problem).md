---
title: "Installation of additional OS (partition problem)"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by freeball1 on 2011-11-10
Hi guys, 

you can see my current partitions on the attached image:
sda1 is ubuntu, sda5 my home folder and sda6 a data partition.

If possible, what is the easiest way to get another bootable OS (win7, winxp or maybe another linux distro) onto the unallocated  54 GB space? Would i have to delete the whole extended partition (sda2) and create completely new partitions?

Thanks in advance.

---

### Post by critin on 2011-11-10
> **freeball1 said:**
> Hi guys, 

you can see my current partitions on the attached image:
sda1 is ubuntu, sda5 my home folder and sda6 a data partition.

If possible, what is the easiest way to get another bootable OS (win7, winxp or maybe another linux distro) onto the unallocated  54 GB space? Would i have to delete the whole extended partition (sda2) and create completely new partitions?

Thanks in advance.

Installing ubuntu in unallocated space is easy and the installer should see the empty space on its own, but Windows is more difficult.  I've never tried it with Windows.

See this link, it seems to have solved their same issue.  I didn't read it so it may be different than your question.

[http://ubuntuforums.org/showthread.php?t=1874903](http://ubuntuforums.org/showthread.php?t=1874903)

---

### Post by freeball1 on 2011-11-26
I finally found the time to back all my stuff up and try to do it. What I ended up doing is resizing the extended partition from a livecd (lengthy process...), so the 55gb section is an own primary partition, then installing win7 and run bootrepair from a livecd again to get grub. 
Worked without any major problems, all data on the extended partition still working.

Marked as solved!

---

