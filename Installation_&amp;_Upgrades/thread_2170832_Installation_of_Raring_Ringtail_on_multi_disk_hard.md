---
title: "Installation of Raring Ringtail on multi disk hardware configuration"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by absunshine99 on 2013-08-27
I wanted to share my experience after running into problems installing Ubuntu 13.04 (64 bit) on my new system. I had two disk drives present, both blank. The system automatically created /dev/sda for the disk I did not want to install to. I chose the alternative of the second disk (/dev/sdb) as the target location and proceeded. I selected LVM configuration but did not choose full manual layout option. Towards the end of the installation when it tried to run grub-install, it tried to write to /dev/sda and failed (the apparently common grub-install /dev/sda failed. This is a fatal error message). Given the option to write to an alternative disk, I tried /dev/sdb (and other /dev/sdb related device files) but it still failed so the installation did not complete properly. A second attempt produced exactly the same results.

I ended up temporarily disconnecting the second disk so the system could only see the one disk on which I wanted to install. This time it installed without a hitch. If other users run into the same problem, I would suggest this physical approach rather than messing around trying different install options and methods. It's a lot quicker.

---

### Post by QIII on 2013-08-27
I've always disconnected other drives.  Helps avoid the significant emotional event of accidentally installing over the disk where you house all your pictures of granny!

---

### Post by absunshine99 on 2013-08-28
It is good advice to disconnect the other drives generally but my experience working with empty disks did uncover what is obviously a bug. Since I did get around it, and I am not in a position to do further testing, I won't be submitting a bug report. However, I am just hoping that anyone who does not think to disconnect the drives may save time if they stumble across my post.

---

