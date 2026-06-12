---
title: "partitioning help"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by guine on 2006-06-24
Im giving dapper one last chance and trying to install dapper onto an existing partition on my harddrive, installing over a dead linux install while leaving a windows partition and swap partition.  I told the partitioner to make it a reiserfs filesystem but the partition is just showing up as unknown filesystem so that I cant install dapper on this partition.  Should I just delete this partition and try making it again or is there something else that I need to do.  Thanks.

---

### Post by Herman on 2006-06-24
> Im giving dapper one last chance and trying to install dapper onto an existing partition on my harddrive, installing over a dead linux install while leaving a windows partition and swap partition. I told the partitioner to make it a reiserfs filesystem but the partition is just showing up as unknown filesystem so that I cant install dapper on this partition. Should I just delete this partition and try making it again or is there something else that I need to do. Thanks. I would definitely make sure I have all the data I want to keep fully backed up.

There must be some reason why the partition is coming up as an unknown filesystem and it might be that you have some kind of corruption in your partition table.
I had a similar thing happen to me a long time ago after testing out a whole lot of different partitioners. They don't all mix very well, I now believe. Now I stick with just the 'Parted family of partitioners and have never had any more problems. I do a lot of re-sizing and partitioning just for testing purposes.
A small glitch in the partition table can remain there for some time and remain dormant until it eventually wipes your whole drive. I re-partitioned and ignored warnings several times before that finally happened. I didn't care because it was only in a test computer, I had no data in it.
I just re-formatted the entire disk and set a new disk label and kept on using the same disk again and the problem never came back, even after many, many partitioning experiments, as long as I keep to the same partitioners. ('Parted based).

So just back up all your data, then delete the partition and then make it again and hope for good luck, Regards, Herman

---

