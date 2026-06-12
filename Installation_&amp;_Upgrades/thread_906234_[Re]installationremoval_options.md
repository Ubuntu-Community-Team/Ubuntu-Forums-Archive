---
title: "[Re]installation/removal options"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by noesquire on 2008-08-31
I first installed Ubuntu onto a partition on my laptop a few months ago. Naturally I wanted to tweak things and experiment with different packages etc. and so inevitably, somewhere along the line I copied in a little too much code which I didn't understand and now the OS is lying in tatters.

I've learnt my lesson from being a Linux noob, but I do find using Ubuntu preferable over Vista, which is installed on another partition. Therefore I'd ideally like to reinstall Ubuntu on the same partition. Am I right in thinking there is no 'roll back' feature with Ubuntu? If I boot from disc and attempt to install again will it overwrite the current build and thus give me a fresh, clean, out-of-the-box install, or will it automatically attempt to partition itself space for a second install?

I also have the capability to basically restore factory settings on my laptop, which I guess I could do to reset the partitions to purely 'Windows' and 'Backup data'. Then I could install Ubuntu again from disc on to a fresh partition.

So there are my options. I want a clean slate with Ubuntu but clearly don't want 2 installs on my machine. I'm a bit nervous to take any action at the moment, so I thought I'd seek out a bit of advice first.

Thanks.

---

### Post by ajgreeny on 2008-08-31
You can do your overwriting first option easily at your installation second attempt.  When you get to the partitioning part of the installation, choose Manual, and then choose the main Ubuntu partition which you already have as your new / (root) partition, and the old swap as the new swap.  Everything will now be overwritten as you hoped and you will end up with a new clean Ubuntu.  If you had a separate /home partition before you can keep that unformatted if you want by ensuring there is no tick in the format button on the page.

This method may just leave you with extra Ubuntu options in the grub menu which don't really point to an installation but appear because there was a Ubuntu which is now overwritten.  They can be edited out later if they do appear, or you can stop that happening this way.  When you get to the live CD desktop, (I'm assuming this is what you used), go to System >> Administration >>Partition Editor and delete the partitions that were used for Ubuntu.  Make sure you get the partitions right as you don't want to delete the Vista partitions.  Now in the space which is free make new partitions of the same size as you had before.  Now install as normal with the partitions you want.

---

