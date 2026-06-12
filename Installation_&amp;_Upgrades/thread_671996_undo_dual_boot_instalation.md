---
title: "undo dual boot instalation"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by umbrart on 2008-01-19
Hello,

Some time ago, my laptop froze up during a system upgrade resulting in it crashing each time I rebooted it. (kubuntu instalation)

Since I didn't want to lose any data on it, made a second kubuntu instalation on it (dual boot after partitioning the hard disk in 2 main parts) and then repaired the first instalation thanks to people on #kubuntu irc.

Now, I have this dual boot that I actualy don't need anymore. If anything, I'd like to just simply restore my system to the old single drive partion (not counting the swap and such) but otherwise I'd be happy to:

- loose the dual boot menu defaulting to my second instalation that I don't use.
- format the partition of the second instalation and mount it in my first instalation so I can use it to store media and savefiles (so next time I get a crash, I can just format the first partition and reinstall there without losing all my data which will be stored on the second partition.)

problems:
- I have no idea how to start on the first one (all threads I found on here about unistalling a dual boot ended up telling how to solve it without uninstalling)
- I get this "hal-storage-fixed-mount refused uid 1000" error when I try to access the second partition.

Any solution to both suggestions are welcome. I do know though that formating the second partition will probably erase the grub on it thus disabling the boot selection menu ending in me not being able to start my computer again so caution is mandatory.

---

### Post by c0met on 2008-01-19
Have you tried booting from the Ubuntu Live CD and running the Partition Manager under System >> Administration to simply remove the Kubuntu partitions? What I'd do is to use the partitioning program to delete the partitions and then create new partitions in that space. This would effectively nuke any files on that partition.

Once problem I anticipate with the above process is that GRUB could be pointing to the Kubuntu partition and after re-creating partitions you might not be able to boot into anything! If that is the case, you would need to reinstall GRUB to get Ubuntu to work. This can be done by using a boot up CD of a program called SuperGRUB from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

If SuperGRUB did not work, you would need to boot from the Live CD and reinstall GRUB.

NOTE: I'm assuming that your Kubuntu /home and your Ubuntu /home are two different directories.

---

### Post by umbrart on 2008-01-19
actually, both are kubuntu partitions.

So if I get it correctly, I can install grub from the live CD, and erase the second partition with the live cd too?

Would this keep my first partition intact? I really don't want to run the risk of losing my data and I don't feel like backing up 70 Gb of data "quickly" to be sure (even though I'll end up doing it if nescessary).

I'll see what I can do with the live CD, though I have no Idea how to get started with GRUB.

Hmmm, wait, I just found this:

[http://ubuntuforums.org/showthread.php?t=671667](http://ubuntuforums.org/showthread.php?t=671667)

I think I'll do what that thread says. Seems pretty doable.

---

### Post by c0met on 2008-01-19
I just had a quick look at that thread. If you lose your GRUB that tells you how to reinstall it. GParted (the partition software on the Live CD) will allow you to work on one partition and will keep the other partition intact. Just be careful that you have the right partition. Also, if GParted closes down when you go "Apply" it's ok. Just restart it and continue working.

---

