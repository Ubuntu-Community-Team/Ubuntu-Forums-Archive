---
title: "New Instalation in Windows XP"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Scalphunter on 2008-04-09
I wanna install Ubuntu 7.10 in a Laptop Dell Inspiron 6400

I download the Partition Magic, when i was checking the disk i see one partition (Dell Media Direct) and Another Partition with NFTS where is the Windows, but i see others partitions, here is the screenshot

[http://img141.imageshack.us/img141/9218/sinttulo4yp9.jpg](http://img141.imageshack.us/img141/9218/sinttulo4yp9.jpg)

I understand that i only can have one extended partition, but there is one already, what can i do? i have one that says unallocated, can i delete that partition?

What can i do with the others, there is data in that partitions because i see all the space is in use, where i must free the space for the ubuntu? next to the NFTS o Next to the other partitions?

Sorry for my english.

---

### Post by mikewhatever on 2008-04-09
It looks like you need another HDD. Under normal circumstances, you'd be resizing C:\, the largest partition, creating partitions for Ubuntu and installing, simple. In your case, I doubt Dell recovery utility for Windows will work if you alter partition setup. It's a different story if you have recovery CDs/DVDs or if you don't care loosing Windows.

---

### Post by Scalphunter on 2008-04-09
I don't care the Dell Restore Utility, i asume is the first partition, the FAT, but them i have that extended partition and i understand i can have only one, what can i do?

---

### Post by Scalphunter on 2008-04-09
Can i put the Swap, Ext3 and FAT 32 inside that Extended? in what order?

---

### Post by mikewhatever on 2008-04-09
> **Scalphunter said:**
> I don't care the Dell Restore Utility, i asume is the first partition, the FAT, but them i have that extended partition and i understand i can have only one, what can i do?

The FAT partition is only 47 Mb, so it can't possibly hold recovery files. I don't know what it's for, could be a boot partition or something. Windows recovery files are most likely on one of the yellow partitions that follow C:\.

> Can i put the Swap, Ext3 and FAT 32 inside that Extended? in what order?

Yes, the order does not matter.

I think the best strategy would be to wait for someone with similar setup to offer help. Recovery/Utility partitions can be quite helpful in troubleshooting or reinstalling Windows.

---

### Post by Scalphunter on 2008-04-09
Well, i don't use the media direct, so i will delete that partition, then i will merge that with the NFTS and the unallocated, resize it, and convert the free space in a extend one, i will create the FAT32 there, let some free space for the Swap and the Ubuntu.

The i will tweak the media direct button doing this 

[http://forum.notebookreview.com/showthread.php?t=182495](http://forum.notebookreview.com/showthread.php?t=182495)

I think that will be enough

What do you think? 

That way i don't need to delete the First partition and the last one that i don't know what it's for

---

### Post by mikewhatever on 2008-04-09
That should probably work. Don't forget to backup your important files. Good luck.

---

### Post by Scalphunter on 2008-04-10
Thanks Mike, now i am in Ubuntu, works fine, i only need to configure my wifi and that's all, it's 2:00am, i will do it tomorrow!

---

