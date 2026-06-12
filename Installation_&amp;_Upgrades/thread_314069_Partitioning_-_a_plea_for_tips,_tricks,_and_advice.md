---
title: "Partitioning - a plea for tips, tricks, and advice."
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by PietreWitobi on 2006-12-07
So I have the following plan for my little 80 gigabyte hard drive.

>4 OSes... (With purpose)
>>Windows XP  (Gaming)
>>Ubuntu,  (Main)
>>Minix,   (OS building/Self-teaching)
>>and a much more bare-bones linux distro (More Self-teaching) Suggestions?
>With a mutual data partition,
>And I believe I need a swap partition (or more than one?)

So I was looking for advice on partition schemes, sizes, filesystems, etc.

I was also wondering if there's a partition editor I could use too preset these partitions before I start installing, Any suggestions there?

I realize this is a bit overkill on the OSes, but I was thinking

>5 gigs per OS, possibly 10 for Windows... total 20-25 gigs, formated in the necessary manner...
>50+ gigs main storage (planning on getting an external drive to supplement this).  (????????  NTFS?  Fat32?  Ext3.  I can get my windows to read Ext3, but it screws with the FileSystem...
>Swap (Really unclear on the demands for this... ellucidaiton would be appreciated.

Thanks... And I hope this is the right place to put this, I debated for a while on where to post.

---

### Post by aysiu on 2006-12-07
I've moved you to the right place.

You may want to read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by PietreWitobi on 2006-12-07
Thanks for the reference article, but It really only deals with the Ubuntu/Windows...  I still have a few questions.

For instance... do I need a swap partition for each Linux distro?  Or will they recognize the same one?

Or the pros/cons of each filesystem, still a little fuzzy.

---

### Post by aysiu on 2006-12-07
You need only one swap partition... period. During installation of each Linux distro, you can specify for the distro to use your shared swap partition.

As for filesystems:
FAT32 - fragmented, no journaling, no support of permissions
NTFS - full write support is almost there but still not as reliable as FAT32
Ext3 - great for Linux but needs [http://www.fs-driver.org](http://www.fs-driver.org) to be read from/written to by Windows

Hope that answers your questions.

---

### Post by PietreWitobi on 2006-12-07
Sweet, thanks.

---

