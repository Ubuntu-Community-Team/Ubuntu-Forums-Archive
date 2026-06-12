---
title: "Install hosed: Possible to Upgrade from Live CD?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by mitch2k2 on 2007-10-17
Hey all,

In the process of trying to resize my Ubuntu partition (made the mistake of doing it in XP with Paragon Partition Manager), I've rendered my installation unbootable. First there was a forced and failed fsck that kept (hundreds of times at least) reporting problems with inode tables or something. Now, it's hosed to the point where Grub can't even find it.

A couple of questions, but first a few details. The Ubuntu Gutsy install is (was) on a bootable external USB drive, but that was working smoothly. Grub is installed on the USB drive. I used Paragon to increase the size of the Ubuntu partition and add a shared NTFS partition in some unallocated space.

Now my questions: first, is there some easy way of rebuilding or otherwise fixing the Ubuntu partition's file system, without needing to reinstall?

Second, short of that, can I simply use the Live CD to upgrade the current install and hopefully fix the problem in the process? To be clear, I can only boot into Ubuntu via the Live CD, so booting into the damaged partition and setting the Live CD as a repository isn't an option.

Third, worst case scenario, can I copy the Home folder from that drive over to another partition and then reinstall Ubuntu fresh and set the home partition there? Or will install overwrite the stuff in my Home folder?

Thanks in advance for any help you can offer.

---

### Post by mitch2k2 on 2007-10-17
One more thing. When running fsck manually from the pre-boot console, I answered yes to the many node errors (relocate?<y>) and now it seems they're all confined to one group, but fsck can't fix these errors and always starts over and finds this same group again and again. 

Sucks.

---

### Post by logos34 on 2007-10-17
There may be a way to get it to boot (testdisk?), but if fsck can't clear up the errors it might be better (and ultimately faster) to reinstall.

As to your other questions:

2. nope, need to use the alternate cd for upgrade
3. Use [this howto]("http://www.psychocats.net/ubuntu/separatehome") to copy existing /home to a separate /home partiton.  When you reinstall make sure the /home is indicated but that 'format?' box is unchecked (do NOT format)

---

