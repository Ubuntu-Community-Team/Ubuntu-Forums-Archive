---
title: "dual boot partition size"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by mattsnowboard on 2008-06-19
So I wanted to try ubuntu on my new laptop with Vista.  I understand how to do it, but I don't know how big I should make my partitions.  I want Vista on one, another for my files to share between the OS's, and of course one for Ubuntu.  So how big should I make these?  I have a 320GB harddrive.  Also, I will probably be installing a lot on both OS's and I don't want to run out of room.

Hoping for some advice here, thanks.

---

### Post by avtolle on 2008-06-19
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) for general partition planning. As to size, that's a good question. Perhaps a 30 GB for Vista, 30 GB for Ubuntu, the balance to the shared data partition? BTW, I usually make a subdivision in my Ubuntu partition, about 10GB for the o/s, 1 GB /swap, and using the 30 total, the balance to /home (although you should, of course, do what you want).

---

### Post by VMC on 2008-06-19
> **mattsnowboard said:**
> So I wanted to try ubuntu on my new laptop with Vista.  I understand how to do it, but I don't know how big I should make my partitions.  I want Vista on one, another for my files to share between the OS's, and of course one for Ubuntu.  So how big should I make these?  I have a 320GB harddrive.  Also, I will probably be installing a lot on both OS's and I don't want to run out of room.

Hoping for some advice here, thanks.

How about splitting them down the middle. Leave a little room for Swap. Maybe 2-3 gb. That depends on size of ram. Linux can read NTFS, so you don't need a separate partition for that unless you want one. As far as Windows reading/writing Linux partitions. Maybe something like this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by SkonesMickLoud on 2008-06-19
Have you looked into [Wubi](http://wubi-installer.org/)?

It allows you to install Ubuntu into Windows without modifying any partitions.

---

### Post by mattsnowboard on 2008-06-19
I have 3gb ram, so 6gb for swap?  And if I want to install a lot of programs in ubuntu as I try it out, will 10GB for the "/" part be enough?  I think I'll make a small /home and then a large shared partition.

---

### Post by mattsnowboard on 2008-06-21
I want to get some advice before I partition, so should I use 6GB for swap (3gb ram), and is 10GB for / good enough to try out a lot of program installs?

Sorry to do that bump, but I really want to make sure I do this right.

---

### Post by logos34 on 2008-06-21
> **mattsnowboard said:**
> I have 3gb ram, so 6gb for swap?  And if I want to install a lot of programs in ubuntu as I try it out, will 10GB for the "/" part be enough?  I think I'll make a small /home and then a large shared partition.

The '2 x ram' rule for swap only applies up the ~1 GB.  Anything beyond that is overkill.  I dare say 2 GB swap should be more than enough for everyday usage.

If a separate /home, then 10 GB for / should be plenty.

---

### Post by mattsnowboard on 2008-06-21
> **logos34 said:**
> The '2 x ram' rule for swap only applies up the ~1 GB.  Anything beyond that is overkill.  I dare say 2 GB swap should be more than enough for everyday usage.

If a separate /home, then 10 GB for / should be plenty.

Ok I think this is the last question.  If I have all my windows vista os/programs alongside my shared documents and media in one partition (whatever is left besides ubuntu), 10GB for /, and 2GB for swap, how much should home be?  I don't need much data on it (main stuff is on vista partition) and I'm new to linux so I don't exactly know what it is used for.  What size should I use?

Thanks for all the help btw.

---

### Post by housam on 2008-06-21
> **mattsnowboard said:**
> Ok I think this is the last question.  If I have all my windows vista os/programs alongside my shared documents and media in one partition (whatever is left besides ubuntu), 10GB for /, and 2GB for swap, how much should home be?  I don't need much data on it (main stuff is on vista partition) and I'm new to linux so I don't exactly know what it is used for.  What size should I use?

Thanks for all the help btw.

For /home partition ,it depends on how much you will store in it as a separate partition. if you create a large enough  NTFS partition as a shared one it is enough and no need for a separate  /home partition because the /  root partition will have a home folder for storage too.
 ALSO for swap i recommend 3 GB = RAM  because you'll need it for hibernation. all the contents of the ram will be transfered to the swap during the hibernation.

You can take a look at this [[COLOR="Red"]_[U]document_[/U][/COLOR]]("http://www.faqs.org/docs/Linux-mini/Partition.html") for partitioning

---

### Post by housam on 2008-06-21
I have a suggestion for your partition table.

50 GB for vista  NTFS primary partition
100 GB for storage 1 NTFS primary partition
100 GB for storage 2 NTFS primary partition
70 GB as an **extended** partition ( which will have the following logical partitions inside it )
50 GB ext3 format for the root (/) logical partition
3 GB for swap logical partition
17 GB ext3 format for /home logical partition

---

### Post by mattsnowboard on 2008-06-21
> **housam said:**
> I have a suggestion for your partition table.

50 GB for vista  NTFS primary partition
100 GB for storage 1 NTFS primary partition
100 GB for storage 2 NTFS primary partition
70 GB as an **extended** partition ( which will have the following logical partitions inside it )
50 GB ext3 format for the root (/) logical partition
3 GB for swap logical partition
17 GB ext3 format for /home logical partition

Could I keep the "storage" 1 and 2 as a single partition of about 200 GB?  That's the only part that doesn't make sense to me, but I like the suggestion.

EDIT:
my harddrive is actually 295 GB (because 320GB is never actually that much).  So should I take the extra space out of the ntfs storage?  Or from some of the /home?
Also, is it worth keeping the 10GB recovery partition that dell gave me by default?  I haven't looked into how well it would work but should/could I remove it?

---

### Post by housam on 2008-06-21
> **mattsnowboard said:**
> Could I keep the "storage" 1 and 2 as a single partition of about 200 GB?  That's the only part that doesn't make sense to me, but I like the suggestion.

EDIT:
my harddrive is actually 295 GB (because 320GB is never actually that much).  So should I take the extra space out of the ntfs storage?  Or from some of the /home?
Also, is it worth keeping the 10GB recovery partition that dell gave me by default?  I haven't looked into how well it would work but should/could I remove it?

I made it 2 storage ntfs just to separate different data on them but you can make them only one and remove the shortage from it . this will be mandatory now because you have another primary partition ( the recovery partition of dell which I recommend to keep it - just in case ).
You  have the right to create only 4 primary partitions on a single HDD or 3 primary and one extended ( which can be divided to many logical partitions )

now you'll have Vista, recovery and storage as a primary partitions and one extended for the rest

---

### Post by mattsnowboard on 2008-06-21
> **housam said:**
> I made it 2 storage ntfs just to separate different data on them but you can make them only one and remove the shortage from it . this will be mandatory now because you have another primary partition ( the recovery partition of dell which I recommend to keep it - just in case ).
You  have the right to create only 4 primary partitions on a single HDD or 3 primary and one extended ( which can be divided to many logical partitions )

now you'll have Vista, recovery and storage as a primary partitions and one extended for the rest

Ok so now I looked into disk manager and found this
86 MB partition EISA configuration
10 GB recovery NTFS
285.5 GB OS (c: drive) NTFS
2.5 GB partition (not visible in my computer, no file system)

So first, how do I know what the 86 MB and 2.5 GB partitions are?
There is some dell media direct software that is supposed to be able to boot separately so I suspect that is involved.  What can I do then if I need these partitions for some reason and the limit is 4 partitions?

Also, when I go to shrink c: in vista, it says 111155MB available shrink space, so is that the smallest I can make it?

Thanks for your help so far.

---

### Post by housam on 2008-06-21
I think those partitions are  for dell utilities . you should ask your dell agent about them and if you can remove any of them. for resizing the C: drive use the vista partitioning tool to get the maximum free space out of it . and if you can't get any more than the 111 GB , there is no problem as you can make the storage smaller and anyway ubuntu detects all the partitions and can access vista partition too. also you can access ubuntu partitions through vista using this driver :[[COLOR="Red"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")

---

### Post by mattsnowboard on 2008-06-21
> **housam said:**
> I think those partitions are  for dell utilities . you should ask your dell agent about them and if you can remove any of them. for resizing the C: drive use the vista partitioning tool to get the maximum free space out of it . and if you can't get any more than the 111 GB , there is no problem as you can make the storage smaller and anyway ubuntu detects all the partitions and can access vista partition too. also you can access ubuntu partitions through vista using this driver :[[COLOR="Red"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")

Ok the partitions are for Media Direct (it can be booted separately and is made to play dvds/music on a laptop without using much battery).

I want to delete the recovery partition, then shrink the vista partition by 60 GB to leave me with 70GB for ubuntu.

The problem now is that the partitions are currently

< 86 MB (Media direct related) > < 10 GB Recovery > < 285 GB Vista > < 2.5 GB Media Direct >

Anyway, if I shrink the vista one and delete the recovery, will it be a problem that there is space before AND after the vista partition? Can I make the vista partition shift back over the recovery partition so that the ubuntu partition can be all together?

---

### Post by logos34 on 2008-06-21
> **housam said:**
> ALSO for swap i recommend 3 GB = RAM  because you'll need it for hibernation. 

you're right--sometimnes I forget this, I hardly ever use hibernation anymore (suspend-to-ram works just fine).

---

### Post by mattsnowboard on 2008-06-21
So do I need to use something like gparted to get rid of the recovery partition and leave space for ubuntu?

---

### Post by housam on 2008-06-22
> Anyway, if I shrink the vista one and delete the recovery, will it be a problem that there is space before AND after the vista partition? Can I make the vista partition shift back over the recovery partition so that the ubuntu partition can be all together? 

It is better to make the Vista in the front of the drive just after that media partition. so, if it can be done with vista partitioning tool to shift to the foreward after deleting the recovery partition,it'll be better. if not Use the Gparted partitioning tool ( on the live cd ) to do the trick. Be aware that shifting vista to the foreward will take a long time.

> **mattsnowboard said:**
> So do I need to use something like gparted to get rid of the recovery partition and leave space for ubuntu?

Yes, you can Do this with Gparted

---

