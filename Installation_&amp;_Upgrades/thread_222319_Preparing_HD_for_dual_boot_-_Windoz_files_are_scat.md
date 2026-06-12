---
title: "Preparing HD for dual boot - Windoz files are scattered"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by JimS on 2006-07-24
...
I want to add Ubuntu to my notebook pc.
The pc already has WinXP.
The HD is 35% full, so there is plenty of room left for a dual
boot configuration.
But when defraging the HD, I discovered that there were "unmovable"
files scattered one end to another.
Is there a way to move these "unmovable" files?
Question: What should I do next?

I been thinking that maybe I must copy everything, including OS
files, using Norton Ghost to a portable HD.
Then wipe the notebook's drive clean.
Then reformat its drive for both WinXP and Ubuntu.
Then ghost the XP partition, using the copied files on the
portable HD
And finally install Ubuntu.
What do you think?
...

---

### Post by Jagot on 2006-07-24
I had some files all over the disk before I installed Ubuntu, but the installer handled it fine.  Have a go - the installer will not go ahead unless it is certain it will succeed.

---

### Post by JimS on 2006-07-24
...
So, you are saying that when I make a second partition; the
first partition, when it is reduced, files are moved and saved,
even "unmovable" files - Right?  

This assumes that the new first partition is still large enought to
hold all the files.

I have a copy of Partition Magic somewhere.
I better start looking for it.
Also I need to decide the sizes and number of the new partitions.

Thanks,

---

### Post by Jagot on 2006-07-24
Don't use Partition Magic.  The Ubuntu installer comes with a partition editor which you should use instead.

Yep, I'm afraid I don't know how it did it, but I had unmovable files left at the very end of my hard disk which I assumed would stop me from reducing the size of the partition, but they did not, and everything on that disk was left intact after resizing.

Have a read of this guide regarding planing the partitions:

[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

---

### Post by JimS on 2006-07-25
Thanks for finding the partitioning guide.
I had seen it some time ago and it was on my mental list of
sites to find again.  Thanks for shortening my search.

I'll copy everything onto a portable HD and then try the way
you described.

---

