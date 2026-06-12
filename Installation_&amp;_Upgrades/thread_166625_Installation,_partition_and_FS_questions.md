---
title: "Installation, partition and FS questions"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by sf. on 2006-04-26
I plan on setting up a new dual boot system with XP and Ubuntu and am looking for some help and advice on how to do it correctly (the first time).

-I'll have atleast two hard drives. Is it better to keep XP and Ubuntu on completely separate drives, or does it not matter at all?
-I'd like to have a partition that both OS's can read/write to. Would it be better to try to do this as NTFS or ext2? I think the file size limit makes FAT32 not an option. 
-How many partitions should be used for Ubuntu? Is it possible for these partitions to be hidden or completely non-accessible to XP? I guess this might depend on what I end up using as a solution for my previous question.

Any help with the above would be greatly appreciated and any other advice would be great too! :)

---

### Post by Sef on 2006-04-26
> I plan on setting up a new dual boot system with XP and Ubuntu and am looking for some help and advice on how to do it correctly (the first time).

Read this excellent tutorial.  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

> -I'll have atleast two hard drives. Is it better to keep XP and Ubuntu on completely separate drives, or does it not matter at all?

It is up to you.

> -I'd like to have a partition that both OS's can read/write to. Would it be better to try to do this as NTFS or ext2? I think the file size limit makes FAT32 not an option.

Use ext2 to share.  Linux can read, but not write to NTFS.

> -How many partitions should be used for Ubuntu?

5 partitions total: 

hda1 - XP
hda2 - Ubuntu
hda3 - Home
hda4 - ext2
hda5 - Swap

Note: One will have to be an extended partition and not a primary.  (Only 4 primary partitions are allowed.)

> Is it possible for these partitions to be hidden or completely non-accessible to XP? I guess this might depend on what I end up using as a solution for my previous question.

Xp won't be able to affect the Linux partition at all.

---

### Post by sf. on 2006-04-26
Thanks for the reply. Is there one Windows ext2 driver that is generally regarded as being better than the others?

---

### Post by Sef on 2006-04-26
> Thanks for the reply. Is there one Windows ext2 driver that is generally regarded as being better than the others?

None to my knowledge.

---

### Post by AdventChildren on 2006-04-27
hello, I'm newb of Linux :) . 1st time I install Ubuntu Linux, I didn't set a swap drive for Linux  :-? .

Isn't will cause any problem when I running Ubuntu whitout swap drive :-? ?

If want to set a swap patition, how much space was needed :-? ?

thank :)

---

### Post by Rxke on 2006-04-27
If you have a lot of memory installed, swap gets little usage, so you might not even notice you didn't install a swap partition...

re: size: there is always a lot of discussion about that, but often swapsize is set to be as big as your physical memory...

---

