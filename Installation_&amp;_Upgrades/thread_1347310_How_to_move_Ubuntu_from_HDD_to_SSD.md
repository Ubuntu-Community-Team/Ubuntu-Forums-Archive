---
title: "How to move Ubuntu from HDD to SSD"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by mfearby on 2009-12-06
How can I go about imaging my existing Linux root partition (/dev/sda1, ext3) from a SATA HDD to a SATA SSD? I know how to use clonezilla to backup/restore, but as for whether Ubuntu will actually cope after the move, that's another story. I recall having to use rdev a long, long, time ago but I'm rather rusty now.

I'll also have to edit fstab to point to the new device file for my home partition, but it's the getting Ubuntu to boot is what I'm not sure about, and I'd like to ask first to make sure this is even possible. 

Does Linux support the TRIM command yet?

thanks :-)

---

### Post by apocalypse80 on 2009-12-06
You will want to align the partitions on the ssd - something not required on a hdd.
I'm not sure if that's possible with clonezilla and I think that it will destroy any pre-existing alignment.

I know that fsarchiver (contained in system rescue cd) works.
How to;
1) Create fsarchiver images of the hdd, separate for each partition.
2) Partition and format the ssd however you wish, making sure the partitions are aligned.
3) Restore the fsarchiver images on the ssd
4) Re-install grub on the ssd from an ubuntu live-cd.

As for trim, there is no automatic trim like there is in windows 7.
What you can get is the wiper tool contained in latest hdparm ; [http://www.ocztechnologyforum.com/forum/showthread.php?t=60882](http://www.ocztechnologyforum.com/forum/showthread.php?t=60882)
That can be automated via cron to run once per day and trim the free space of ext3/4 partitions.
In case you have an intel ssd, like me, the process of getting this to work is somewhat more complicated.

---

### Post by matt06 on 2009-12-06
> **apocalypse80 said:**
> You will want to align the partitions on the ssd - something not required on a hdd.
I'm not sure if that's possible with clonezilla and I think that it will destroy any pre-existing alignment.

Can you elaborate or give me a good link about aligning partitions on SSDs?  I googled, but man there is a plethora of multipaged results dealing with a variety of topics.

A nutshell please?  Why, pros, cons??

---

### Post by mfearby on 2009-12-06
> **matt06 said:**
> Can you elaborate or give me a good link about aligning partitions on SSDs?  I googled, but man there is a plethora of multipaged results dealing with a variety of topics.

A nutshell please?  Why, pros, cons??

Thanks apocalypse80 for the info. I think I agree with matt06, though. I've never heard the term "aligning partitions" before.

I guess I could also just do a fresh install since my /home partition is separate from my root partition. The only things I'd need to backup would be anything related to Apache and MySQL, presumably. Not much else installed that I would care about if lost.

I've got a G.Skill Falcon II 128GB on the way. Pity about there not being automatic TRIM support in Linux yet, however, since most changeable stuff will be kept on /home (HDD, not SSD) then I shouldn't need to run a clean-up regularly, I would think?

---

### Post by apocalypse80 on 2009-12-06
Some reading on alignment; 
[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)
[http://www.ocztechnologyforum.com/forum/showthread.php?p=325221](http://www.ocztechnologyforum.com/forum/showthread.php?p=325221)

The easiest way to create aligned partitions; connect the ssd to a pc running win7, create all partitions (unformatted) then boot from an ubuntu live cd and format them using gparted.
Win7 will only create aligned partitions.

There are no cons whatsoever, only pros.
Specifically there's a performance advantage.

Almost all image/restore programs will destroy any pre-existing alignment because they delete the old partition.
fsarchiver does not change partition geometry, therefore an aligned partition remains aligned.

---

### Post by matt06 on 2009-12-07
wow, not sure if I could wrap my head all around that, but thanks for the links.

So alignment is not necessarily required then but should be done if at all possible.

---

### Post by rsay on 2010-03-06
I found some good information on the following link:

[UNIXgod's Official UNIX/Linux SSD Guide]("http://forums.extremeoverclocking.com/showthread.php?p=3599469")

---

