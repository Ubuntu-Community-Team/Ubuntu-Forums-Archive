---
title: "Repartitioning over an installation"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by deNoobius on 2008-06-22
I've had numerous issues installing Ubuntu on my laptop, posted in other threads.  Where I am now, I rebooted from the live CD, which had me install some new firmware, and everything works great as long as I stay with the live CD.

My theory is that if I reinstall from the working live CD, I'll have better results this time around.  My original install, on a 60 GB hard drive, allocated 20 GB to Windows and 40 to Ubuntu. 

On reinstall, the partitioner wants to create two new Ubuntu partitions.  It does not "see" the Windows partition at all, and recomends 8 GB for the first Ubuntu partition and the remaining 32 GB for the second.  

1.  Is this an OK allocation?

2.  Will I love my ability to boot into Windows, which I need to do sometimes?

Thanks.

---

### Post by deNoobius on 2008-06-24
Is there anyway to uninstall Ubuntu and restore my original setup short of buying Windows Vista? (the computer is an hand-me-down and I didn't get the OS on disk).

---

### Post by Partyboi2 on 2008-06-24
If you have vista still installed on your system you can use [[COLOR=Blue]this[/COLOR]]("http://www.arsgeek.com/?p=3340") to restore the mbr (master boot record) using the  ubuntu live cd. Then after this boot the ubuntu live cd again and use gparted (System>Admin>Partition Editor) to delete your ubuntu partitions.

---

### Post by deNoobius on 2008-06-25
Thanks, this would be a nice solution.  One of the required steps is to apt-get install a program called ms-sys from the repositories, but none of the standard repositories, including universe, seems to have it.  

Do you (or anyone) happen to know where I can get it?  Is there a repository that I have to add at the command line?  Thanks again.

---

### Post by Partyboi2 on 2008-06-25
Sorry that package is not in the hardy repos you can download and install the package from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/gutsy/ms-sys")

---

### Post by deNoobius on 2008-06-25
OK, great, I'll try that this evening.  Thanks!

---

