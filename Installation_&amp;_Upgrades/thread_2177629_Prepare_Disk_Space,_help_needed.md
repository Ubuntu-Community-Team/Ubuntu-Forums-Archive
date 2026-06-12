---
title: "Prepare Disk Space, help needed"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2013-09-29
I'm in the middle of 1st attempt at installing xubunyu dapper drake on my ancient emachine 5414 laptop.

I'm doing a full install, there is an older version of Ubuntu on HD.

I'm at the , Prepare Disk Space, How do you want to partition  the disk?

1. Resize IDE 1 master, partition 1 (hdall) and use freed space?

2. Erase entire disk; IDE1 master (hdal) - 100.o GB Hitachi HT SS41210H9AT00

3. Manually (I don't want to do this).

Below these questions is, New Partition Size; 52% (47.0GB)

Mike

---

### Post by Dreamer Fithp Apprentice on 2013-09-29
I'd do 3, even if you don't want to. Learn to want to. :)

Actually, if you don't want to keep the old installation, first I'd boot the old installation, or if it won't boot - boot a live disk instead, and make absolutely sure there is no data on there you need to keep. Stuff in home, on the desktop, in the downloads folder perhaps? Browser bookmarks maybe? Scripts you stuck somewhere not obvious, like /bin, maybe?

Then if there isn't or if you have copied it on to external media, you can do # 1.

If you don't want to keep the old installation, but there is stuff you want to save and external media isn't handy, I'd boot up a live disk in live disk mode rather than installer mode (I don't know if dapper had that -- that's a REAL old edition you've got there). Then I'd use gparted to shrink the partition on there and then make a data partition. Then I'd copy what you want to save onto it.

Then, what I'd do would depend on how much RAM you have and how much drive space. You might want to delete the partition that was on there and make 2 partions out of it, one for /, and one for swap. If you have plenty of RAM I wouldn't bother with swap. 

Then I'd run the installer. Your options will look different when you do. Not sure what they will be. Dapper was a long time ago. Post back it doesn't seem obvious what to do at the time.

Are you sure you want to use an edition that hasn't been supported for such a long time? You might think about  Lubuntu if the idea is to be get good use of a low resource system. 

Sounds like you have plenty of disk space to do anything you want. If there is nothing on there you want to keep, you can of course pick # 2. Personally I'd stll do manual, #3. Because I think the default setup is just plain dumb. A lot of things are simpler if you keep your data on a seperate partition. And if you have lots of RAM you don't need a swap unless you want to hibernate or suspend. I'm not sure if hibernation or suspending requires some kind of hardware support. If it does they may not be possible on an old machine anyway. Dunno, I've never used either.

If the old system works, personally I'd use the live disk in live disk mode, not installer mode, to run gparted and shrink that partition to maybe 25 gig or, it it has too much stuff to squeeze it down to that maybe 1 gig more than the minimum. Then I'd make another primary partition of about 25 gigs, formatted ext3 for the new system, a third small primary one for swap only if you think you might want it, and a 4th and final partition, which could be extended if you think you might want more partitions later, for a data partition. Then I'd install the new system to the second partition. That way in the worst case you'll still have the system that is on there now to boot from if something goes wrong with the installation. Unless you need the disk space it is always nice to have a 2nd system you can boot from in case one breaks. If the new system works well you might later want to replace whatever is on the 1st partition with something newer since you imply it is even older that Drake.

---

