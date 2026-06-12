---
title: "Windows XP gone after installing Ubuntu 8.04!!"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by thedudething on 2008-09-12
I installed Ubuntu 8.04 on my friends PC, now windows XP is gone completely. You can't even access Windows XP files and there is no /sda under media and there is no boot menu.

Help?

---

### Post by ad_267 on 2008-09-12
Can you open up a terminal (Applications - Accessories - Terminal) and post the output of "sudo fdisk -l". That should show all your hard drives and partitions.

---

### Post by iaculallad on 2008-09-12
How did you use the Gparted utility? Had you selected the option of using the entire drive in you partitioning scheme?

---

### Post by thedudething on 2008-09-12
first off, I can't go on my friends terminal, he doesn't have internet working.

secondly yes we used the entire drive on the partitioning scheme

---

### Post by iaculallad on 2008-09-12
> **thedudething said:**
> first off, I can't go on my friends terminal, he doesn't have internet working.

-Terminal would still work even if you don't have an Internet connection.

> **thedudething said:**
> secondly yes we used the entire drive on the partitioning scheme

That would be bad in your case as selecting the entire drive would let Gparted format that drive and auto partition it. (you're windoze would probably be gone)

---

### Post by ad_267 on 2008-09-12
> **thedudething said:**
> first off, I can't go on my friends terminal, he doesn't have internet working.

secondly yes we used the entire drive on the partitioning scheme

You don't need the internet to open a terminal. And if you choose "use the entire hard drive" then Ubuntu wipes the Windows partition and installs over the whole hard drive, so there's not much change the Windows partition is still there.

---

### Post by thedudething on 2008-09-12
By no internet i mean he cannot contact me in any way other than text, I know terminal still works.

---

### Post by thedudething on 2008-09-12
he says all that came up after doing that terminal thing was stuff like "linux, extended, linux swap/solaris"

Is there anyway to find the windows without using the terminal?

---

### Post by iaculallad on 2008-09-12
> **thedudething said:**
> he says all that came up after doing that terminal thing was stuff like "linux, extended, linux swap/solaris"

Is there anyway to find the windows without using the terminal?

Don't try further on finding your windoze xp partition as fdisk utility did not even reflect any ntfs partition in the system.

---

### Post by ad_267 on 2008-09-12
If there was a windows partition it would say "HPFS/NTFS" or something similar, possibly a FAT32. I think it's long gone sorry.

---

### Post by c2006 on 2008-09-12
> **thedudething said:**
> first off, I can't go on my friends terminal, he doesn't have internet working.

**secondly yes we used the entire drive on the partitioning scheme**

Is there only one hard drive inside the computer?

If so, I hope he has an XP CD... Because if there's only one drive, XP is *goooooone*.

If it makes you feel any better, I've done this exact thing (accidentally installed Ubuntu on my Windows partition/drive) once. Thankfully I DID have the Windoze CD.

---

### Post by Sef on 2008-09-12
What you need is [test disk]("http://www.cgsecurity.org/wiki/TestDisk").

> **TestDisk** is a *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy. 

Don't use the computer that windows was erased on.  It may be possible to recover XP.  However, the more that hard drive is used the less likely you can recover the partition.

---

### Post by slmouradian on 2008-09-12
Good luck using test disk and please report with your results.

---

