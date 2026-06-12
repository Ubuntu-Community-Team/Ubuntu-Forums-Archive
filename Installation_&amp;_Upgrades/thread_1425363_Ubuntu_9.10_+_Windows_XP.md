---
title: "Ubuntu 9.10 + Windows XP"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by connorthecreator on 2010-03-09
I'm trying to duel boot Ubuntu and XP on my mothers old laptop, (not too old, but old). I'm running into 1 main problem, I can't figure out what I need to do to Partition the drive.

any help will be loved ^^

---

### Post by sikander3786 on 2010-03-09
With Windows XP intalled first, all you need is to have some free space on the HDD. Say 20 GB. Leave it unpartitioned and then boot into Ubuntu CD. On the partition options list, select Guided - Use Largest Contiguous Free Space.

Follow the setup and you will have Ubuntu installed with GRUB listing both Ubuntu and Windows XP for dual booting.

Post back if you have any questions.

Regards.

Sikander.

---

### Post by kansasnoob on 2010-03-09
See if this is helpful:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by sinurge on 2010-03-09
> **connorthecreator said:**
> I'm trying to duel boot Ubuntu and XP on my mothers old laptop, (not too old, but old). I'm running into 1 main problem, I can't figure out what I need to do to Partition the drive.

any help will be loved ^^
Free up up some space in windows 
Create a new partition there
use this guide [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by connorthecreator on 2010-03-09
I've tried that, but I doesn't want to partition it, I know there 30GBs free...

---

### Post by Mark Phelps on 2010-03-09
Is that 30GB "unallocated" space -- as in not inside a partition? OR is that 30GB "free space" -- as in, already inside a partition?

If the latter, you will need to shrink that partition before you can use that space for a new partition.

---

### Post by connorthecreator on 2010-03-09
how do I go about shrinking the partition?

---

### Post by akand074 on 2010-03-09
The thing is, windows limits you on how small you can make its partition, I would boot into the ubuntu live CD and use Gparted to do the partition (just shrink the drive and it will become unallocated space). Or preferably you could just manually partition drives during the installation which isn't ideal for beginners but I can explain it for you: 

-Start the installation of ubuntu, follow the steps (keyboard layout and such) 
-when the partition manager starts, it'll ask if you want to do a guided partition and such, the last step will say "Manually select partitions" check that and click next and the partition manager will open.
-Click on your windows partition and shrink it (change the amount of space down about 21GB should be fine)
-You should now have 21GB as unallocated space. Click on it and set the file format as EXT4, size to 20GB and mount point as "/" just the slash without quotations.
-Set the last 1GB left as unallocated space as SWAP area, thats all you have to do for that one
-Format both the linux partition and swap but make sure NOT to format the windows partition (make sure it is NOT checked)
-click next and let the installation go. 

Hope either way helps.

---

### Post by connorthecreator on 2010-03-09
no luck, After 10 minutes it gives me an error message saying "An error occurred while writing the changes to the Storage Device.

The resize operation has been aborted."

---

### Post by connorthecreator on 2010-03-09
bump

---

### Post by akand074 on 2010-03-09
Sorry I had a Lab to go to, so what did you try to do that gave the error message? It could just be that Windows needs the little free space you have left. Windows is very picky like that.

---

### Post by connorthecreator on 2010-03-09
I followed the instructions you gave me, then I got the error. (it didn't even get to 1%.

---

