---
title: "Vista Formatted Ubuntu Partition!!!!"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Lacrimstein on 2008-06-22
Some classes that I will be taking in college require the use of windows, and using wine is not an option (until it fully supports Visual Studio), so today I installed Vista on a partition I set aside for it. It installed perfectly, but now my Ubuntu partition seems to have been wiped. It shows up as unallocated space in gparted in the LiveCD. Why vista touched a partition it wasn't supposed to is a good question to ask of microsoft, but as of now I am looking for some sort of a recovery solution so I can get at least a part of my data back. Can someone please help?

---

### Post by Rhubarb on 2008-06-22
You could try testdisk (it's available in the Ubuntu repos)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If your data is very important to you, take out the hard drive and send it to a specialised data recovery center.

If you have some hard drives (the same size or larger), copy the entire hard drive to a backup.

If you're willing to try testdisk, (it's a command line app that looks a bit ugly, but does the job quite well).
Get a different big hard disk, install ubuntu on it / run the Ubuntu live CD.
Install testdisk, mount the blank hard drive so you have write access to it.
Make sure your hard drive (to be recovered - the one that used to have Ubuntu on it) is NOT mounted.
Then run testdisk (**man testdisk** for details)

If your data is important to you, and you're not confident about what you're doing, send it to a data recovery specialist.

---

### Post by anthonie on 2008-06-22
I second that, TestDisk is quite usefull as I have recovered a lost partition with it twice. However, you're probably working on Vista and you may want to try the Windows version of it, although I do not know whether it works on Vista. I've only tried it on XP to recover a couple of files but it works equally well on Windows.

If that does not work for you, you may want to have a look at a program like GetDataBack, but this is commercial software and the free version has limited functionality.

[http://www.runtime.org/](http://www.runtime.org/)

Good luck and be nice to your machine while it's working at it...

---

### Post by WeeWoh on 2008-06-22
Try Disk Internals Linux Reader and the Linux Recovery. I accidentally converted my disk type to dynamic and lost my coursework and they worked fine to recover the files. I still havent got the space back though...

---

### Post by Pumalite on 2008-06-22
You can also try rescuecd (it comes with TestDisk):
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Burn to disk and boot from it.

---

