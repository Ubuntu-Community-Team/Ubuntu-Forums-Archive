---
title: "Quick Question!"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by luckyfox on 2010-01-24
Can someone please help me real quick.

Ubuntu has decided on the following setup for reasons I am unsure of.
[U]
Obviously,[/U] this will need to be adjusted, as I need more than the remaining 712.5 MB for all of my documents.. What would you suggest?

sda1 is assigned to XPPro.

/dev/sda1      | ntfs__ ______ | /media/disk1|    33      GB
/dev/sda2      | ext2________          | /media/disk |  260     GB
/dev/sda3      | extended____   |___________|      5.33 GB
=> /dev/sda5 | ext3_____ | / _________|     3.33 GB
=> /dev/sda6 | linux-swap |__________                   |     2      GB

Feel free to quote and adjust to your suggested sizes.

---

### Post by darkod on 2010-01-24
> **luckyfox said:**
> Can someone please help me real quick.

Ubuntu has decided on the following setup for reasons I am unsure of.
[U]
Obviously,[/U] this will need to be adjusted, as I need more than the remaining 712.5 MB for all of my documents.. What would you suggest?

sda1 is assigned to XPPro.

/dev/sda1      | ntfs__ ______ | /media/disk1|    33      GB
/dev/sda2      | ext2________          | /media/disk |  260     GB
/dev/sda3      | extended____   |___________|      5.33 GB
=> /dev/sda5 | ext3_____ | / _________|     3.33 GB
=> /dev/sda6 | linux-swap |__________                   |     2      GB

Feel free to quote and adjust to your suggested sizes.

I am assuming you had the /dev/sda2 already existing there and maybe you even planned to use that for ubuntu?
The thing with creating partitions in advance is, that you ALWAYS have to go into manual partitioning in step 4 of the installer, and TELL ubuntu you want to use an existing partition for /, swap, /home, or what ever. Just because there is ext2 partition it WILL NOT take it by default.
On the contrary, it will assume you need it and it won't touch it.

In case you wanted to install in /dev/sda2 it's probably best to do:
Boot with the ubuntu cd, Try Ubuntu option, open Gparted and delete the newly created /dev/sda5 and /dev/sda6, then /dev/sda3. Note, the swap, /dev/sda6 will probably be mounted, with keys symbol next to it in Gparted. You have to right-click it and select Swapoff to be able to delete it.

After that is done, delete /dev/sda2 also (if there is no data on it). Don't forget in Gparted you need to click the big green tick mark button in the toolbar to execute the scheduled commands.

After all of that your disk should remain with /dev/sda1 and the rest unallocated space, not belonging to any partition.

Boot with ubuntu cd, Install Ubuntu option, and use Use Largest Available Free space option. That will set it up in the unallocated space. Or create partitions manually if you prefer.

---

### Post by dE_logics on 2010-01-24
Yes, Ubuntu has not done right selecting that root partition...it's too small.

Why not first partition the disk in Windows or with Ubuntu live CD and then try and install?

Then you can select directly in which partition Ubuntu will need to be installed after to the manual configuration in the partitioning section.

---

### Post by luckyfox on 2010-01-24
@[darkod]("http://ubuntuforums.org/member.php?u=946366") Thanks for the OMEGA basic instructions.

And upon thinking back, yes.
That was supposed to be the idea (that obviously worked well, right? =**FAIL**).

**On a side note**, I have a secondary drive on this PC. Microsoft will talk to it fine, but Ubuntu keeps thinking WTF? It recognizes the junk I have on it as 'unknown' space, and the remaining space on it as unallocated space. What in the devil is ***that*** about?

---

### Post by luckyfox on 2010-01-24
> **dE_logics said:**
> Why not first partition the disk in Windows or with Ubuntu live CD and then try and install?

Then you can select directly in which partition Ubuntu will need to be installed after to the manual configuration in the partitioning section.

I think that was supposed to be the original idea, and I (***obviously***) wasn't paying attention.

---

### Post by darkod on 2010-01-24
> **dE_logics said:**
> 
Why not first partition the disk in Windows 

Stay away from this if planning to install linux. Windows will only create ntfs partition which is even worse than creating ext4 partition in advance. At least you can tell the ubuntu installer to use it as root for example. You can't tell it to use ntfs partition as root.

Yes, you could use Gparted in live desktop, that's the preferred way to handle partitions, but my recommendation stands to leave the space as unallocated and let the ubuntu installer use it like that. It will create the necessary partitions.

---

### Post by luckyfox on 2010-01-24
> **darkod said:**
> Stay away from this if planning to install linux. Windows will only create ntfs partition which is even worse than creating ext4 partition in advance.

Got the whole mess sorted out, and now have TONS of GB to work with in my documents! THANKS!

---

