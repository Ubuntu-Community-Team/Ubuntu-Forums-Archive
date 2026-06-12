---
title: "installing on dell 'backup' partition"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by prem1er on 2007-05-10
I was wondering if it would be easier to install Ubuntu on the 20g partition that Dell has already created for me, rather than removing both partitions and starting from scratch.  Is this possible/a good idea?  Or should I use PartitionMagic and remove both partitions to resize them how I see fit?   Thanks.

---

### Post by scrooge_74 on 2007-05-10
You dont need to use partition magic.  The Live CD has its own partition tool call Gparted.

You can either use the backup partition or create new ones without erasing the XP partition.

My advice to you is to divide the 20 GB partition into at least to so your Linux system is in one and the /home folder is in the other.  That way if you latter have to reinstall all your documents and info are going to be safe and sound on their own partition

---

### Post by prem1er on 2007-05-10
Oh, I forgot to mention.  I have an external with all a Windows backup in case anything goes wrong.  But I can just install Ubuntu on the 20gig backup and I should be ok?

---

### Post by scrooge_74 on 2007-05-11
Yeah sure, you can use the 20 GB for your install, in 10 years I never used those backup spaces I always used to move my data out of the partition where Windows was in case I had to re-install windows (lots of times over the years)

---

