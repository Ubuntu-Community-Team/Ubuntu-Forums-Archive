---
title: "dual boot with 1 hard drive (SOLVED)"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by joe209 on 2016-04-25
Hello. I am looking to make a dual boot with xp and Ubuntu mate 16.04.

The only thing is that I only have 1 hard drive and can't make a partition as it is mounted.

I don't have a cd to make a live gparted. Is there any other way I can make a partition which Ubuntu can recognise and install onto?

Any help and advice would be much appreciated.

Thanks!

---

### Post by ajgreeny on 2016-04-25
How are you trying to install Ubuntu?  If you are using a live USB, which is what I would advise, you will find gparted on the OS that you are then running which you can use.

However, I am not sure if XP has its own disk management tool to shrink a partition, but if it has, you should use that to shrink the Windows partition after defragging it a couple of times.  In the times that I dual booted I also turned of virtual memory in Windows before defragging, but I'm not sure if that is really helpful or not.

If XP does not have its own shrinage tool use gparted from the live Ubuntu, but make sure you shrink the partition from the right end only; do not move the starting point of the partition or you may have problems booting it.  Also run chkdisk in Windows after shrinking it before installing Ubuntu into the now unallocated space.

DO NOT create any partitions with Windows that you will use for Ubuntu; that can cause problems as the partitions may not be correct for a Linux OS, and Windows can not create, nor can it read ext4 partitions.

For more info on installing see:-
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389) 
and
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by joe209 on 2016-04-25
Hi ajgreeny. I'm using unetbootin as Tha is my only option. The problem is that I can't make a partition using gparted because I only have 1 hardrive and you can't edit or unmount!

---

### Post by sammiev on 2016-04-25
Hi joe,

You can use the gparted from a live install to make the required changes.

The question is, can you boot from a USB/DVD?

---

### Post by joe209 on 2016-04-25
Thanks very much for the replies, much appreciated! I managed to download gparted on unetbootin and boot it up using ram!! 
Thanks again guys.

---

