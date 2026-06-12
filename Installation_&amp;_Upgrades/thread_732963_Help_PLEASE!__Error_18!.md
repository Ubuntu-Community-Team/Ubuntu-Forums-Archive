---
title: "Help PLEASE!  Error 18!"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by DoogH on 2008-03-23
So, I just installed linux to a new partition with windows on the other.  However, my computer is now getting a GRUB Error 18 and cannot boot up.  I have a 1TB drive, and this could be the problem, or it could be my BIOS (from my understanding).  Please help me fix this issue, I need my computer back ASAP.

---

### Post by Pumalite on 2008-03-23
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
This usually means the need to create a /boot partition at the beginning of your drive. Others in this forum know more about this than I.
Your BIOS has limit on the size of the drive.
[http://ubuntuforums.org/showthread.php?t=607047](http://ubuntuforums.org/showthread.php?t=607047)

---

### Post by DoogH on 2008-03-23
Oh jeeze...  If I used Linux's partitioner instead of Vista's, am I screwed?

---

### Post by Pumalite on 2008-03-23
You just have to start again. Fix your Vista MBR with Super Grub:[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then allocate space for Ubuntu with Vista partitioner FIRST. Then install Ubuntu. You might have to look into that issue of your BIOS.

---

### Post by DoogH on 2008-03-23
Nah, vista worked on my 1 TB drive.  I did have to download a BIOS update to get vista to work, but one of the changes was "Updated BIOS to support harddrives over 1TB"

---

### Post by DoogH on 2008-03-23
Wait...  Why don't my current partitions work?

Windows boots up fine...  What is better about the Windows Partitioner?

---

### Post by Pumalite on 2008-03-23
Post:
sudo fdisk -lu

---

### Post by DoogH on 2008-03-23
What?

I am currently back in windows, but not sure why windows partitioning is better.

---

