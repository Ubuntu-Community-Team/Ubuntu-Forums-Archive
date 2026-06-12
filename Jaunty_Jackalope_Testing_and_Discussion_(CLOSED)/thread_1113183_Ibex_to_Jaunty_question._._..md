---
title: "Ibex to Jaunty question. . ."
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nmdrg on 2009-04-01
I currently run the "latest" version of Ubuntu, 8.10 Intrepid Ibex.

I am happily awaiting my soon eventual upgrade to Jaunty Jackalope, 9.04.

But I am wondering, in fear and in wonder, for my searches elsewhere have come up with no answer, whether or not, the EXT3 filesystem will become EXT4 during the upgrade or will i need to do a fresh install just wondering to make sure I don't have to do a fresh install and make my own apt-on disk kind of thing.


once again the question: While upgrading from 8.10 to 9.04, will the EXT3 file system upgrade to EXT4?

thanks

---

### Post by redbob on 2009-04-01
Well, I'm using Jaunty since Alpha 4 into my laptop, now I'm with Beta.
My laptop has 3 partitions, system I choose to format under ext4, but other partitions, that were already ext3 when I was using Intrepid, remain ext3 until now.

---

### Post by ZorgTheDestroyer on 2009-04-01
Not that I know much about it. But I can't imagine that your filesystem is upgraded if you not do a clean install.

---

### Post by Therion on 2009-04-01
Even if you do a fresh install, during the partitioning and formatting you have to *specifically* change from the default filesystem of Ext3, to "get" Ext4 formatting.

---

### Post by redbob on 2009-04-01
That's right. It's nonsense that any instalation could change partition formatting without at least asking for approval. When I'd installed Windows NT over Windows 95, the instalator ask if I wanted to convert FAT32 to NTFS.

---

