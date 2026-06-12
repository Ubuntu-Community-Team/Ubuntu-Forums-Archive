---
title: "Installation crashed while trying to replace WIN-XP from UBUNTU 12.10"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by Deepesh Deepak on 2013-04-09
I was trying to replace windows xp from ubuntu 12.10 with a memory stick.After the installation started it immediately crashed and a message of "Installation crashed" appeared.Now after this ,I restarted the pc and got nothing ,no previous windows xp ... only a cursor blinks. Now I want to recover data from the hard disk,or if possible recover previous windows installation.Will installation of win-xp can recover data? 

What are the ways to recover data-photos,videos and other files ?

---

### Post by darkod on 2013-04-09
Replace windows from ubuntu? Did you actually tried to install windows while booted into ubuntu?

You don't install any OS like that, especially not windows. You need to boot from the cd and install it like that. But now if you make a new installation it most probably will delete the existing one with all the data. Depends where your data was/is.

You can try recovering partitions with testdisk. Do the Deep Search and see if the reported partitions look like something you expect. You can also try listing files on partitions with P.
After you are sure all partitions are detected and can be recovered, change the characteristic of the partitions as you need and write the new partition table. But only then and not before!

[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Deepesh Deepak on 2013-04-09
No. I had windows xp installed previoulsly and I was trying to replace it by ubuntu. While installing from bootable ubuntu USB stick , there comes options of installing ubuntu "alongside windows" or "replace it by ubuntu" ! I just selected "replace it by ubuntu" and pressed continue.Then about 10 seconds later a message popped up saying "Installation Crashed".Then I restarted the pc and got no OS, only a cursor is blinking.

Now , I want to recover my files.I want to know whether previous partition of hard disk is left or not ?. If it is left then whether installation of windows xp again can recover my files or not ?

Or simply put whether I have the option of recovering my files or not . If there are possibilities then please help.

---

### Post by darkod on 2013-04-09
There is, you can try recovering the XP partition(s) using testdisk as mentioned above.

But I don't understand this data recovery. Are you aware the "replace it by ubuntu" option would have deleted all your data anyway, if it succeeded to install? That option deletes the other OS (in this case XP), repartitions the hdd and deletes all data on it, as far as I know.

So, if you needed to get some data out, you should have done it before starting all this.

Try testdisk and see what the deep search comes up with.

---

