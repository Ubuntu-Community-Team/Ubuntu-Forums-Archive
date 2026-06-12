---
title: "Trouble getting Lucid dual boot installation on hard drive with errors and XP install"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by aextance on 2010-10-23
I'm trying to create a dual-boot system, and have been following the instructions [here]("https://help.ubuntu.com/community/WindowsDualBoot").

However my hard disk has bad sectors, and GParted won't let me resize the Windows partition. It tells me to use ntfsresize with --bad-sectors as an option, after having done some checks, all of which I've done. I've successfully shrunk the NTFS volume in this way - when I boot into Windows, it says the hard drive is the size I set it at. However, the Ubuntu installer and Gparted still see the Windows partition taking up the entire hard drive.

So, for the installation, do I have to set the size of the volumes manually, or is there a way to make Ubuntu see what ntfsresize has done?

---

### Post by mikewhatever on 2010-10-23
Setting partitions manually shouldn't be necessary, and, since it can't see the changes you've made, would probably fail. Make a good backup before experimenting.

---

### Post by Jozza The Wick on 2010-10-24
Hey aextance,

Yeah, I feel your pain. This was my first install of Ubuntu, and unfortunately it was the most painful, because the machine had sooooo many hardware problems! This thread details what I had to do - using fdisk to delete and create a new partition that starts at the same cylinder on the disk but is smaller. Done properly, it doesn't affect the Windows partition.

Details are here:

[http://ubuntuforums.org/showthread.php?t=1244058](http://ubuntuforums.org/showthread.php?t=1244058)

Good luck!

As a happy ending, when I upgraded 7.04 (dual boot) to 10.04 (whole disk) on that same machine, it was the smoothest OS install I've ever had - and it runs faster!

---

