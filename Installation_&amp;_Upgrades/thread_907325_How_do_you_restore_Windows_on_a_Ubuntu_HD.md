---
title: "How do you restore Windows on a Ubuntu HD?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by GregWI on 2008-09-01
Using a dual hard drive system, one hard drive for Windows XP/SP3 and one hard drive for Ubuntu 8.04.  Ubuntu recognizes the Windows hard drive, but Windows will not recognize the Ubuntu hard drive. Windows command line won't even recognize it.  If a hard drive has Ubuntu on it, and say you want to return it to a Windows recognizable state, where as you can reformat that hard drive in Windows, how do you do that?

---

### Post by stonecoldking on 2008-09-01
Taken from: [http://www.linuxquestions.org/questions/linux-general-1/accessing-linux-hard-drive-from-windows-224332/]("http://www.linuxquestions.org/questions/linux-general-1/accessing-linux-hard-drive-from-windows-224332/")

> Try this:

[http://www.ibiblio.org/filesystems/h...s-HOWTO-6.html](http://www.ibiblio.org/filesystems/h...s-HOWTO-6.html)
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

Boby

Have a look at the two sites he mentions for accessing it through windows.

As for formatting it... i couldn't say of the top of my head but see if u can delete the Unidentifiable space occupied by Ubuntu (the Ubuntu partition) on XP through... Control Panel -> Administrative tools then look for disk management. Then to use that free space format it into NTFS (or FAT?¿) 

(oh! and btw, Just to cover my ***: this will delete all data on your Ubuntu partition!!)

---

