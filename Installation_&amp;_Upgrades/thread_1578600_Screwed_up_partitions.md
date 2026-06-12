---
title: "Screwed up partitions"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by MegaLoler on 2010-09-20
I was going to reinstall ubuntu on a pc.  It already had ubuntu on it, but It was an old version and instead of updating it several version I wanted to just start fresh.  So I went into windows and used A partition manager of some kind ( i dont remeber what it was called)  to delete the partitions that had ubuntu on it.  I guess that was a mistake, because now when I boot it the computer goes into grub rescue, and I dont know what to do.  I booted it from the live cd and mounted the harddrive, and the windows data is still there.  When I run gpart, it doesnt detect any partitions.  Just /dev/sda/.  I do not want to erase the whole disk, because i need the windows data and I do not have the windows install disk.

So anyway to fix the partitions?  :(

---

### Post by perspectoff on 2010-09-20
> **MegaLoler said:**
> I was going to reinstall ubuntu on a pc.  It already had ubuntu on it, but It was an old version and instead of updating it several version I wanted to just start fresh.  So I went into windows and used A partition manager of some kind ( i dont remeber what it was called)  to delete the partitions that had ubuntu on it.  I guess that was a mistake, because now when I boot it the computer goes into grub rescue, and I dont know what to do.  I booted it from the live cd and mounted the harddrive, and the windows data is still there.  When I run gpart, it doesnt detect any partitions.  Just /dev/sda/.  I do not want to erase the whole disk, because i need the windows data and I do not have the windows install disk.

So anyway to fix the partitions?  :(

The Grub bootloader was in the Ubuntu partition you deleted. When you reinstall Ubuntu, a new copy of Grub will be installed. You probably won't have any problems if you just go through the automatic Ubuntu installation process again (just don't install to the whole disk drive, which would then erase your Windows partition). The Ubuntu installer ought to help you create a new partition for Ubuntu usage from the free space left behind when you deleted the old Ubuntu partition. In fact, you can just use the option to "install in existing free space" without worries.

At the end of the Ubuntu re-installation, Grub will be reinstalled and it will automatically locate the Windows partition and OS. Your boot menu will again be created (showing both Ubuntu and Windows), and you will again be in business, just like before (but with a new Ubuntu installation, obviously).

---

### Post by MegaLoler on 2010-09-20
But that option isnt available, and it says "this computer has no operating systems on it"
thanks for replying

---

### Post by MegaLoler on 2010-09-20
Would it be good to Run the gparted live cd and try to recover the partition table?  I will try that.

---

### Post by MegaLoler on 2010-09-20
It worked!  The ubuntu live cd detects the partitions now, and that option you mentioned is available now.  So when it installs it should fix grub like you said :D  thanks!

---

