---
title: "Partition Screw-up"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by stryker719 on 2007-06-06
First I want to say I'm very excited to give ubuntu a try.  I've been looking for a more user-friendly version of Linux and ubuntu seems to be the solution.

However, I made an error when trying to partition my drive that I'd like to resolve.

I have two hard disks on my computer; a 150gb disk that is used for my Windows Vista OS, and the second is a 400gb secondary onto which I wanted to install ubuntu, and which currently has all of my music, photos, etc.

When I was using the Manual Partition tool in ubuntu, I somehow screwed up the 400gb drive.  I reduced the total size to 200gb, with the other 200gb unallocated.  However, when I boot up ubuntu and try to resize the partition into its full size, I am unable to.

The program states that drive's full size, 400gb, but says there is only 50gb of unused space.  This makes sense, as I have 150gb of data.  My question is how to I resize the partition to the full 400gb?

Once I do that, I will create a new partition for ubuntu that is around 80gb.  

I'm sorry if this doesn't make any sense, but as you have probably already guessed I'm new to this.

Thanks for your help.

---

### Post by NeoLithium on 2007-06-06
The best way is to boot back in to your liveCD, and resize the partition with that; just write your changes to disk and it should return to the original size for you :)

---

### Post by stryker719 on 2007-06-06
Thanks for the quick response.  I'm in ubuntu now, using the GParted partition manager.  I can't make any changes to the partition, as there's a locked symbol next to the drive.  Any thoughts?

---

### Post by merlinus on 2007-06-06
It would seem that the partition is mounted, so it cannot be changed.

Try gparted live cd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

