---
title: "Windows 10 installer wrecked my partition table"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by doug16k on 2015-08-09
In my setup, I have several partitions, and not all space is consumed. The last two partitions were physically at the end of the disk. I told the windows 10 setup program to make a new partition in a gap before the last two partitions. It took forever to say that there was an error formatting the new partition. After rebooting the partitions that were after that empty space were all deleted.

I tried a couple of things, but the testdisk package is what solved it for me. It found all the abandoned partitions quickly and wrote a completely fixed partition table.

---

### Post by Mark Phelps on 2015-08-09
So unfortunately, you found out the hard way that the Win10 installer messes around with the existing hard drive partitions.

Before try the upgrade again, if you want any chance of going back to the current Windows version on the PC, then download and install the free version of Macrium Reflect and use it to image off the Windows partitions to an external drive.  ALso use the option to make a boot CD.

That way, if Win10 trashes your PC (as it is know to do in too many cases), you will have a way to restore a working version of Windows.

---

