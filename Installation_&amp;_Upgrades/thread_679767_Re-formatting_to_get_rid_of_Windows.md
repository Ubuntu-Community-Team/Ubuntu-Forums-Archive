---
title: "Re-formatting to get rid of Windows"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by joshdudeha on 2008-01-27
Here's a description of my system.
Grub Bootloader with the following OS's installed:
 >Kubuntu 6.06
 >Ubuntu  6.06
 >Windows XP
My family is on about getting a new computer soon, which will almost certainly have Vista on it, so I'm thinking of keeping this computer and just having Ubuntu on it. 
I'd love to just re-format now and get rid of windows, because I, myself, have no intention of ever using it again. 
But, I can't get rid of it 'til we get this new computer. That way, my family will be able to use Windows and won't have to learn anything new, while I use ubuntu.
Thing is, once i re-format the Windows partition, I don't think GRUB will load because it won't be able to find the Windows partition.
Would my ubuntu still load up if I got rid of Windows, or would I have to do a clean install (which I may do when 8.04 comes out).
Thanks for the help.
Also, I'm thinking of buying a new hard drive, as I need more space.
Would an average say, 60GB IDE (i don't have much money atm lol) work ok with Ubuntu?
Thanks again.
Joshx

---

### Post by Pumalite on 2008-01-27
You can erase the Windows partition and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Your new hard drive should be fine.

---

### Post by browndruid on 2008-01-27
What I would suggest is to burn a copy of the[ Linux Rescue Disk]("http://www.sysresccd.org/Main_Page") and boot from that, then get into GParted. From there, you could delete the windows partition (which should be NTFS, I believe), and merge that empty space onto the existing partitions in whichever way you like. Of course, backup your system first.

---

### Post by Pumalite on 2008-01-27
You can do it with Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize any partition you see fit. Backing Up is something you should do always when installing new systems or manipulating partitions.

---

### Post by browndruid on 2008-01-27
> **Pumalite said:**
> You can do it with Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize any partition you see fit. Backing Up is something you should do always when installing new systems or manipulating partitions.

Didn't know it could be simpler that what I had learned. That's awesome, thanks!

---

### Post by Pumalite on 2008-01-27
You are welcome. Good luck. Keep Gparted around, it will come in handy in many occasions

---

### Post by joshdudeha on 2008-01-27
One more question,
might sound stupid.
But first : how do i find out what interface my hard drives are
and is ATA the same as IDE?

---

### Post by Pumalite on 2008-01-27
ATA is IDE

---

### Post by joshdudeha on 2008-01-27
Ah sorry for my mis-understanding
do you know how to find out the interface of a hard drive
?
thanks

---

### Post by Pumalite on 2008-01-27
What do you mean?

---

### Post by joshdudeha on 2008-01-27
Well
I'm pretty sure my hard drives are IDE
because this computers a few years old.
But, just in case i buy an ATA one and end up having a different interface.
Idk,

---

### Post by joshdudeha on 2008-01-27
Ah don't worry.
I just looked in Device Manager
and they are IDE Disks , thanks for the help

---

### Post by browndruid on 2008-01-27
I think he might mean the formatting, like ext 3 or NTFS. GParted will tell you that when you open it up.

Ignore that, I didn't read the second  page by mistake.

---

