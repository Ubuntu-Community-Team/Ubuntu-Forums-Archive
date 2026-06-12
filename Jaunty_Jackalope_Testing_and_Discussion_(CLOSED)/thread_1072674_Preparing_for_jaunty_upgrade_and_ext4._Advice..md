---
title: "Preparing for jaunty upgrade and ext4. Advice."
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Belerophon on 2009-02-17
Hi.

Since Jaunty will support ext4, I am doing some research on how I can later UPGRADE to Jaunty and make FULL use of the ext4 advantages.

I've seen many info on how to migrate from ext3 to ext4, but this seems not to be ideal as the old files remain in the old format.

So, I was wondering if this method works:

- upgrade from intrepid to jaunty;
- boot live-cd and copy EVERYTHING under "/" to some place else, external drive for example;
- use live-cd to COMPLETELY format hard drive and create new partition in EXT4 format;
- copy everything back to "/";
- change everything that is needed under fstab and menu.lst;
- boot system again.

Does this work?
And by the way, is there a method that migrates ext3 to ext4 including the existing files?

---

### Post by whoop on 2009-02-17
Wow, that method seems very scary to me. Might mess up your permissions to say the least.
I'm hoping that e4defrag will be available when I upgrade to Jaunty and that it does what I hope that it does (defrag the ext4 partition untill it is truly ext4)

---

### Post by Belerophon on 2009-02-18
> **whoop said:**
> Wow, that method seems very scary to me. Might mess up your permissions to say the least.
I'm hoping that e4defrag will be available when I upgrade to Jaunty and that it does what I hope that it does (defrag the ext4 partition untill it is truly ext4)

So, you do not advise me to do it.
Is there some kind of software, like Partimage, which can help me in the backup operation, so that I can later restore the information without messing up the permissions?
Unfortunately, Partimage does not support ext4.

And that e4defrag? What do you mean by "be available"? Is it a tool still in development or what?

---

### Post by whoop on 2009-02-18
> **Belerophon said:**
> So, you do not advise me to do it.
Is there some kind of software, like Partimage, which can help me in the backup operation, so that I can later restore the information without messing up the permissions?
Unfortunately, Partimage does not support ext4.

And that e4defrag? What do you mean by "be available"? Is it a tool still in development or what?

Well, in the least I can say that I wouldn't do it. I am aware that there are tools to make a complete backup of a partition, these tools can restore this partition as well. The point is that we would like to restore the partition in a new format. I don't think that exists (yet).

e4defrag is the defragmenter for ext4. Last time I was running jaunty it wasn't available (yet). I also heard somewhere that this might be kernel related and that e4defrag will be supported in the next upcoming kernel.

I am not even sure that e4defrag will do what we want it to do. But I can imagine that once an ext3 partition is converted to an ext4 partition; you can boot a live-cd with e4defrag and defrag the entire partition to a true ext4 partition. This works flawlessly in my mind :D

If there are no further developments I will probably upgrade, convert my partition to ext4 and wait for tools to come available.
It is also nice to note that every time I update an application/package (after the conversion) I will not only update the program but also make it faster; as every newly (over)written file will use true ext4 technology. So if you wait long enough, the problem will solve itself ;-)

---

### Post by Belerophon on 2009-02-18
> If there are no further developments I will probably upgrade, convert my partition to ext4 and wait for tools to come available.
It is also nice to note that every time I update an application/package (after the conversion) I will not only update the program but also make it faster; as every newly (over)written file will use true ext4 technology. So if you wait long enough, the problem will solve itself

Yes, I understand...and either way, it's what I'm going to do when the time comes to upgrade...I'm too lazy to do a clean install.

But still, for those of us who want to squeeze out all of the performance we can from the system, having those old files and folders not "tuned up", is very frustrating...

Thank very much for the explanations ;)

---

### Post by truls.pingen on 2009-02-23
The above stated recepie works great for backup. 
A fe pointer that might make it easier:
Use tar, and use l to stay inside one partition and p to preserve file permissions.

If you have a backup of your partition, you can easily reformat the partition in whatever format you want.

---

### Post by mgol on 2009-02-23
truls.pingen is right, use tar (I'd use bzip2 also, to make a smaller *.tar.bz2 file). In this way no permissions will be broken.

---

### Post by Belerophon on 2009-02-23
Thanks a lot for the tip! :D

...and besides the permissions, there isn't any other problem?

---

### Post by mgol on 2009-02-23
> **Belerophon said:**
> ...and besides the permissions, there isn't any other problem?

Shouldn't be. But remember to make this backup **NOT** from Your actual system, as it can differ from its natural state (some temp files, additional devices, etc. etc.). I'd use LiveCD Ubuntu to make a backup.

I cannot see any other threat, it should be OK now.

---

### Post by nxsty on 2009-03-11
You don't need to do all that to migrate to ext4. Ext4 is backward compatible with the ext3 disk format so all you need to do is to mount your ext3 filesystem as ext4 (edit /etc/fstab and reboot). You can later use tune2fs to turn on new ext4 features, but then you need to do a full fsck and wont be able to mount the filesystem as ext3 any more. Only new files created will use the extents feature though.

---

