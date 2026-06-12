---
title: "improper partition recognition"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by rumblefishubu on 2010-01-12
When i install and run gpart in ubuntu9.10, 
     or the gparted live cd, 
     or clonezilla,

my harddrive which currently has a 200 meg unused portion
                                                 a 830 gig primary partition "C:" ( win764 )
                                                 and ~100 gigs of open space

((and all this is seen correctly by windows disk manager))

is read by any linux tool and lists the drive as having a 200meg partition
                                                       a ~36 gig primary partition
                                                      and ~850 gigs of free space.

MY GOAL is to have the drive read by linux tools in the same manner it is recognized by windows.


*a bit of history.  this is a triple boot win764, ubuntu9.1064 and snow leopard machine.

i have two identical 1tb western digital black drives on which i used clonezilla to copy the primary drive to the test bed drive and that is the one which i have used to attempt installs and upon success clone back to the first drive, or upon failure clone the workable drive back to the test one, and start a different direction.

it was at this point that i had the second drive partitioned correctly and i was going to simply clone the working windows partition (fail safe hd) into the new partition on the test drive.

to my suprize clonzilla, and any ubuntu tool like gpart, wouldn't read the source hd partitions correctly.

or it is, 

somehow how windows and linux tools read a drive for partition information got disconnected.

my hope is someone has an idea, maybe from windows cmd line, of how to force windows to rewrite it's partition information to disk.

thanks for your time, 1st ubuntu forum post, have used many forum posts, didn't post any specs b.c i don't think they are needed.

---

### Post by phillw on 2010-01-12
Hi & welcome to the forum.

Whichever way I try to do the maths, it doesn't work !!

When you format a 1TB drive, you're going to have in the order of 950MB usable space.

So, start at 950 MB, then subtract what you say you have ..... You very quickly run into a minus figure.

If you want to get the mbr re-set to Win (which I *think* is one of the things you wanted) then head over to here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That will put Win back in charge. Once you're booting Win okay, post back what it thinks that it has - bearing in mind it **has** to be less than 1000MB !! 

Regards,

Phill.

---

### Post by rumblefishubu on 2010-01-12
Once you're booting Win okay, post back what it thinks that it has - bearing in mind it **has** to be less than 1000MB !! 

Regards,

Phill.




thanks phill, here is the thing,  windows boots fine.  windows says i have 88ish gigs free
at the end of the partition

but if i fire up a ubuntu9.10 live cd and get ready to partition,
it thinks most of the drive is free.  ubuntu sees a 200meg partition, then a 38ish gig partition, then 800 plus gigs of open space...

which is totally wrong... ubuntu should see a 200 meg partition and a 800plus gig partition (where windows is currently, and functioning properly mind you)
and ~88 gigs of free space.


thanks for the link to the other 
i really don't have any bootloader issues.  its just like windows is created its own partitions and ubuntu see's the correct and current partitions.  it reports back with arbitrary sizes from some long lost different formatting senario.

this is a puzzler... i haven't found, read, or seen anything like it.

---

