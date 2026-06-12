---
title: "VirtualBox Installation Problems"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by helixed on 2007-06-16
Hey everybody,

I'm currently trying to install a VM Windows XP copy on an external hard drive of mine.  The hard drive gets through most of the main install fine, but I'm using a copy of Windows XP which came with my laptop (It's a Dell), and as a result it tries to install a few more applications specifically relating to its own hardware, which is fine.  At first I tried formatting my external hard drive with the ext3 file system, but I received permission errors when trying to access the files on it, so instead I reformatted the hard drive to the fat32 filesystem.  Now, I've tried installing Windows XP in VirtualBox twice, and I keep getting the same error when it gets to the Dell applications install.  I receive the following from VirtualBox:

Host system reported that the file size limit has been exceeded. VM execution is suspended. You need to move the file to a filesystem which allows bigger files.


Error ID: 
DevATA_FILETOOBIG
Severity: 
Non-Fatal Error

Is this because I'm using the fat32 filesystem, and if so how should I format my external hard drive?

Thanks,

Helixed

---

### Post by helixed on 2007-06-17
Anybody?

Thanks,

Helixed

---

### Post by mrphantastic on 2007-06-17
you're EXACTLY right, you CANNOT use FAT32, i just read on another thread that the max filesize for any type of file on that system would be 4gigabytes.  You need to use something different on your external to run xp.  By the way, running a virtual machine  -  from an external location, will probably be rough and very laggy.  Just a forethought...

---

### Post by helixed on 2007-06-17
I read in another post it was hard on your hdd to run two OSs off of it.  It's the same idea as copying two files at once, the hard drive heads can't keep up.  I bought the external hard drive to make up for this, as I can't put a second hard drive in my laptop.

Helixed

---

