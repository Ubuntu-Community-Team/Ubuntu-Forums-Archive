---
title: "Dual booting with XP, drives already partitioned"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by phoenixankit on 2007-05-29
I have an 80GB HD, which is dev into 4 20GB partitions. One of them is completely empty(20GB). Can someone please tell me STEP BY STEP instructions on how to dual boot XP w/ubuntu.
I did somethings on my own, and I reached the partition stage. What to do after that, ie what options to select


This is the problem I encountered :

So, I managed to get the Ubuntu installation till this page:
][[IMG]http://www.imagefilez.com/out.php/i109662_29052007.jpg[/IMG]](http://www.imagefilez.com)


What to do next? I have around 20GB of free space(not allocated to any drive) so, as far as I know, I need to create a Linux swap partition of around 1GB first in that 20GB space. when I do this, this comes:
[[IMG]http://www.imagefilez.com/out.php/i109663_29052007002.jpg[/IMG]](http://www.imagefilez.com)

What options do i have to select?As far as I know
1)Primary or Logical?(i dont know what to fill)
2)Space will be arnd 1000MB for the swap partition
3)Beginning or end?(i dont know what to dill)
4)I have to select swap(cuz i'm creating a linux swap)
5)Some one told me that i hv to select swap in the 5th one also, but if I select swap in the 4th one, the 5th one becomes grey.



Please tell the steps after this also...


Thanks in advance
~Ubuntu n00b

---

### Post by tommcd on 2007-05-29
You will have to select logical partitions. You can only have 4 primary, so if you try to make swap primary you then have 4 so that is likely why #5 gets grayed out.
Choose "manually edit partition table".For swap select logical, file sytem swap, mount point swap, size 1GB. Choose beginning if it asks.For root, select logical, file system ext3, mount point /. Choose beginning also, and use up the rest of the space on that 20GB free space. You could also make root around 8-10GB. Then you could use the rest for a seperate /home. Choose logical again, file system ext3, and mount point /home.
See this site:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) Lots of beginner friendly help there.

---

### Post by phoenixankit on 2007-05-29
> **tommcd said:**
> You will have to select logical partitions. You can only have 4 primary, so if you try to make swap primary you then have 4 so that is likely why #5 gets grayed out.
Choose "manually edit partition table".For swap select logical, file sytem swap, mount point swap, size 1GB. Choose beginning if it asks.For root, select logical, file system ext3, mount point /. Choose beginning also, and use up the rest of the space on that 20GB free space. You could also make root around 8-10GB. Then you could use the rest for a seperate /home. Choose logical again, file system ext3, and mount point /home.
See this site:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) Lots of beginner friendly help there.

THAT is the problem, for swap, If file system is set to swap, mount point gets greyed out(logical is selected)

---

### Post by Bigdog60 on 2007-05-29
dude you are doing it wrong you have to select logical partions.

---

### Post by phoenixankit on 2007-05-29
I tried again. The 5th one still greys out.

HELP PLEEEEEEEEEEEASE

---

### Post by tommcd on 2007-05-29
If you have 3 primary you should be able to select logical for the rest and make as many partitions as you want.  Choose "manually edit partition table". Then delete the empty 20GB empty partition.  This will create 20GB free space. Select to create new partition, logical, size 8GB, file system ext3, mount point /. (Lets see what happens if you make root partition first). The create swap partition, logical again, file system swap, mount point swap, size 1GB. Then use up the rest of the space for /home partition, logical,  file system /ext3, mount point /home. Also check out the link I gave you to the psychocats site.

---

### Post by phoenixankit on 2007-05-30
Ok, I'll try making the root partition first. But I still think when I make swap, mount point will get greyed out...

---

