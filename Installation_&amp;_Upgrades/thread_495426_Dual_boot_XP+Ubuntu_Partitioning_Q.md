---
title: "Dual boot XP+Ubuntu: Partitioning Q"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by Katz on 2007-07-08
Hi,

I'm planning to try to isntall Ubuntu with old XP installation on my desktop. I have a quesiton about partitioning the HDD. The thumbnail shows my HDD partitions at the moment.

Now, I am not sure about how to proceed here. This is what I've thought I should do:

1: Move My Documents all the way to the left, right next to the XP:boot partition.
2: Shrink the extended partition so that it leaves ~15Gbs room for a new Primary partition to install Ubuntu on.
3: Create the Linux installatin partition (EXT3) at the end of the HDD (as a Primary partition)
4: Add following to the Extended partition:
[LIST]
[*]Linux Swap-partition (5 Gb)
[*]FAT32 Partition for exchangind data between XP and Ubuntu (30 Gb)
[*]HOME+other directories for the Ubuntu (EXT3, 100Gb)
[/LIST]

Can I have some comments about this arrangement?
Any problems or newbish mistakes that might trash my rig (I am planning to backup the My documents, I have an other 300Gb HDD available)

Also I've read that it might be sensible to create more partitions for linux for different kinds of stuff on Linux (/usr, /home, /var...) Any suggestions about that?

Thanks in advance.

Oh and is there any way to reduce the time it takes to move the 'My documents'? I did it once and it took like 4 hours. Maybe shrink it, move it in smaller chunk and resize it again at new spot? I'm using the GParted for it.

ps.From my earlier thread, I got my laptop running nicely with Ubuntu (IBM a20m 700) thanks for the help guys and gals :)

---

### Post by confused57 on 2007-07-08
Here's an excellent guide for planning partitions:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
and
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Ubuntu has no problem being installed on an logical partition...you probably don't need your swap to be more than 1.5 Gb.../home would be the only directory you'd need on a separate partition.

---

### Post by Katz on 2007-07-08
Thanks for the links. I have to look into them a bit more. The first one I actually browsed through once, but couldn't find the page anymore.

Oh well, I gotta keep working for a few more hours and when I get home I'm gonna give this installation an other try. Of course then I do have the problem of ATI X1950Pro to deal with too...

---

### Post by Katz on 2007-07-08
Just about to head home to retry the Ubuntu installation and I just thought up an other question about Extended partitions.

The Extended partition is tied to one Primary partition. Now what happens if I format the Primary partition. Does it affect the Extended partition?

I am asking this because I have an image of the Primary partition (XP boot Partition). And I'm planning to drop the older image on that partition sometime soon to get rid of the unnecessary stuff that's found it's way there.

---

### Post by luvr on 2007-07-08
> **Katz said:**
> Now what happens if I format the Primary partition. Does it affect the Extended partition?
No, formatting the Primary partition won't affect the Extended partition, since they're separate. You can safely restore an old image onto your Primary partition, and you won't run into problems.

---

