---
title: "Can't use all space on HDD after uninstalling Kubuntu"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by klokwyze on 2006-11-19
Windows Explorer can only "see" 66 GB of my Maxtor 80GB drive. This  is because I created a 2nd partition when installing kubuntu. I have since deleted that partition.

Partition Magic 8.0 shows that the Drive is one whole partition with a size of about 80 GB, but windows XP can only recognize 66 GB of it.

How can I consolidate all the available space on the one partition and have Windows XP recognize all the space? I would like to avoid a total reformat of the drive if possible.

oh yeah, i uninstalled GRUB using windows recovery console and "fixmbr". So technically Kubuntu is still there, but I want to delete it, etc... btw I am trying to do a fresh install of Ubuntu Dapper after this is done.

THANKS!

---

### Post by Dr. Nick on 2006-11-19
do you want to re-arrange your partitions? technically you should be able to fresh install dapper over kubuntu by formatting the kubuntu partition in the dapper install.

Otherwise you would need to use partition magic to format the kubuntu partition to something windows recognizes like fat32 or ntfs

---

### Post by klokwyze on 2006-11-19
Yeah Partition magic shows my windows partition as being 80GB, but windows only recognizes it as being 66GB. So I can't use partition magic to make windows OR the ubuntu installer "see" the unallocated disk space. I figure if I can get windows to "see" it then the ubuntu installer will also see it.

TBH the ubuntu disc partitioner is a little confusing for me and I don't want to ruin my harddrive forcing me to do a re-format.

---

### Post by Dr. Nick on 2006-11-19
Are you using the desktop or alternate cd? I think the desktop cd is gui partitioner similar to partition magic. The ubuntu installer should see all 80 gb even if windows doesnt, though I dont know why partition magic would say its 80gb when its not.

If you mess with the partition in the ubuntu install just make sure no ntfs or fat32 partitions are touched and windows should be fine

---

### Post by klokwyze on 2006-11-20
im using some DVD iso i downloaded off isohunt. Ill just mess around with the ubuntu partioner and hope I don't destroy my 1st partition.

thanks for all your help!!!

---

### Post by klokwyze on 2006-11-20
I can't seem to fix the problem using the ubuntu disk partition program either.... it calls this extra disc space "unallocated". So.... How do I add this space to the windows partition?

---

### Post by Dr. Nick on 2006-11-20
not sure if you can, i never have tried.

Try to create a ntfs partiton on it and windows should see it.

IF you have xp pro open the control panel and hit administrative tools and then disk management and that may let you do a few things, dont think the tool is in xp home though

---

### Post by klokwyze on 2006-11-21
Funny.... that administrative disk tool recognizes that 9.xx GB is unallocated, but won't give me the option to just add it on to the primary partition.

I then tried creating a new partition of this "unallocated" space. voila! its partitioned! Not.

I put "create new partition" for the exact size of the unallocated space and it "shows" a new partition, but windows cant recognize it.

I even go to create a new partition with partition magic and EVERYTIME it asks me to restart. When I come back to Windows, nothing happened. EVERY TIME.

I kind of just want to say **** it, and do a reformat of the drive, but other people use this computer (even though its mine I still think it would be inconsiderate of me).

Should I just forget it and move on with 9.xxGB less space on my drive?

---

### Post by klokwyze on 2006-11-21
BTW dr. nick thanks for all your help so far. :mrgreen:

---

### Post by Dr. Nick on 2006-11-21
Thats odd, Not sure what you  could do. May just have to mess with it a bit, I think the windows tool allows you to format it aswell if you havent tried that yet

---

