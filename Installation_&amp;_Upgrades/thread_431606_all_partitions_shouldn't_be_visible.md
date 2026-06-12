---
title: "all partitions shouldn't be visible"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2007-05-03
Is there any way of avoiding having all the partitions on my disk appear in Places and the Disk Mounter applet?
I would prefer to have only the partitions with entries in fstab visible. 
The others (I generally have about 12-16 partitions) I really don't want visible from Ubuntu at all.

This was not an issue in Dapper, but has become a "feature" of Feisty.

---

### Post by sandman55 on 2007-05-03
> **undecidable said:**
> Is there any way of avoiding having all the partitions on my disk appear in Places and the Disk Mounter applet?
I would prefer to have only the partitions with entries in fstab visible. 
The others (I generally have about 12-16 partitions) I really don't want visible from Ubuntu at all.

This was not an issue in Dapper, but has become a "feature" of Feisty.

I might not be fully understanding you but what I do is first back up fstab then in fstab put a # in front of any partitions I dont want to mount then I reboot and they are gone

---

### Post by undecidable on 2007-05-03
sandman55

I think you understand but the answer does not work in Feisty.
The partitions that appear already have no entries in the fstab.  

Yet they still appear in Places and in the Disk Mounter.
This did not happen in Dapper.

---

### Post by mikewhatever on 2007-05-03
There is a similar thread you might want to follow [http://ubuntuforums.org/showthread.php?t=428196](http://ubuntuforums.org/showthread.php?t=428196)
They found no solution yet, so you are welcome to provide one. Beware that the initial poster seems to be rather aggressively demanding.

---

### Post by sandman55 on 2007-05-03
I get the picture now and looking in my Places/Computer there are all my partitions I've edited out (I havent had cause to go there since my Feisty install) and looking at the link mikewhatever has left it might be the norm. 
I wonder if its deliberate as I believe Feisty can read and write to NTFS partitions (I still go through my Fat32)

---

### Post by undecidable on 2007-05-03
> **mikewhatever said:**
> There is a similar thread you might want to follow [http://ubuntuforums.org/showthread.php?t=428196](http://ubuntuforums.org/showthread.php?t=428196)
They found no solution yet, so you are welcome to provide one. Beware that the initial poster seems to be rather aggressively demanding.

Ah, thankyou.   As long as I know it is a bug and not klingons messing with my head. 
Apologies I did not see the other post before (I did a search but the database claimed it wasn't working)

My own view is that it is related to the other issue I posted about in
[http://ubuntuforums.org/showthread.php?t=428224](http://ubuntuforums.org/showthread.php?t=428224)
which is that noauto in fstab still results in the partiton being mounted.

---

