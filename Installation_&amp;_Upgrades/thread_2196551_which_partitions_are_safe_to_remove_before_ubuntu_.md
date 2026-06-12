---
title: "which partitions are safe to remove before ubuntu install?"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by LinuxVirgin2000 on 2013-12-30
please see the attached picture of the partitions on my laptop.

I have just bought an ultra book running windows 8.1 and as you can see the SSD is not very big, I want to delete as many of the non essential partitions as i can before installing ubuntu (dual boot) to free up space. 

I am going to delete the 10.78 GB recovery partition because I have already made a Recovery USB drive.

There are also 2 other recover partitions (one is 350MB and the other 450MB) are these safe to delete? I have no idea what they do?

There is also an 8GB partition and I have no idea what its for but it says its 100% free? does anyone think its a bad idea to remove?

also I would appreciate some opinions on whether it is a bad Idea to dual boot with such a small SSD as I have, after sorting out all the partitioning there will probably only be around 50GB for windows and 50GB for Ubnutu (12.04 LTS) is this enough?

---

### Post by Rockiger on 2013-12-30
I wouldn't delete them, maybe Windows need them.

If your SSD is big enough is up to your usage. If you watch a lot of movies it will not be enough otherwise is should be enough. I have a lot of software installed and I am fine with a 10 GB  partition.

---

### Post by grahammechanical on 2013-12-30
All of those partitions are listed as 100% free. Trying doing whatever it is Windows users have to do in order to have something to recover to. Make a system backup or something like that and see if those partitions get used.

As for Ubuntu it will install into less than 10GB. So, 50GB for Ubuntu is massive. Of course it all depends on the amount of data that will be collected. I find 25GB for Ubuntu to be plenty but then again I have another massive partition where I store all my data. At the moment Windows is taking up just over 27GB. That amount will increase if you install applications. So, 50GB seems more than plenty. 

Are you planning a common data partition that can be accessed both in Windows and Ubuntu?

Regards.

---

### Post by Mark Phelps on 2013-12-30
Even if you do make an image backup of Win8 to an external drive, and then remove the Recovery partition (no longer needing it) -- that will only get you 10GB of space, which is really tight!

Your better approach would be to use Win8 Disk Management to shrink the OS partition to make some room.

After that, it would be good to make an image backup of the shrunken Win8 -- so you have something to restore from if the Ubuntu install goes badly.

---

