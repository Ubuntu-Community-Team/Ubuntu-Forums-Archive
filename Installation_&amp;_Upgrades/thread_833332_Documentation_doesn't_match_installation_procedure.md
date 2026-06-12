---
title: "Documentation doesn't match installation procedure"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by OnionTerror on 2008-06-18
Hi, newbie here. I'm trying to install Ubuntu 8.04 and I'm following the documentation to to a dual-boot but it doesn't match what you actually get and I don't know what I should be doing.
From the prepare partitions screen, I am supposed to 'right click Windows partition and select resize'. This is not an option, I can only edit or delete the partition. What should I do? 
Basically, I want to install Ubuntu in say 8Gb of space (I have 30Gb free on the primary disk) but I can't see how to do the 'swap space' partition and the rest. Please help!

---

### Post by pytheas22 on 2008-06-18
I don't recall ever having to right-click, so the documentation you're reading could be old or wrong.

When you get to the partitioning section, you should be able to just left-click on the bar at the end of your Windows partition and drag it to the left to reduce the size of the Windows partition.  You could also use the edit partition option to do the same thing (by specifying how large you want Windows to be).  Once you've freed space by shrinking the Windows partition, you can use the blank space to create swap and / partitions for Ubuntu.

Try it again and see if you can figure it out based on this information.  If you still can't get it, let me know and I'll post screenshots showing where you need to click, as I understand that the stuff above can sound confusing if you've never done it before.

---

### Post by OnionTerror on 2008-06-18
Thanks for replying. Well, I'm told to choose the 'manual' option to partition for a dual boot which doesn't give me the slider. The only time I've seen the slider, it is to resize my external hard drive which obviously isn't what I want to use.

I'm using the documentation given on the ubuntu site itself.
I'll reboot and try shrinking the Windows partition then. Cheers.

---

### Post by OnionTerror on 2008-06-18
I've tried doing that but it comes out with an error. My primary disk is 120GB capacity with about 85Gb used for Windows. I tried resizing it to 105Gb and it didn't work. Should I set the mount point to anything or leave it blank?

---

