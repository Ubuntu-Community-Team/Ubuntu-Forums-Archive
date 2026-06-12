---
title: "Installation Froze?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Mydree on 2007-03-06
eMachines model T2742
Intel Celeron 2.7 GHz processor
256 + 512  MB DDR RAM PC2700
40 GB hard drive
Wifi card: D-Link DWL-G520
Windows XP
Note: I recently added the extra 512 MB RAM and wifi card. 

I ran Ubuntu 6.10 from the CD and everything seemed to work (internet, audio, etc.).

Then I decided to install Ubuntu. At Step 5, I chose "Re-size Partition". 

It seemed to be working properly but then after an hour or so it seemed to stop. The hard drive stopped all activity and the screen remained the same (the cursor/disc was spinning). I let it sit for another hour and still no change. 

I clicked "Cancel" and the spinning disc changed back to an arrow but nothing else happened. 

I powered down, re-booted and Windows XP came back after I removed the Ubuntu installer disk and after Windows ran check disk. However now my HD under Windows is now just 20 GB (instead of 40 GB), so it looks like the installer re-sized the partition and then froze. 

Any suggestions? 

More info: [My Ubuntu Linux Project]("http://mydree.newsvine.com/_news/2007/02/26/586704-my-ubuntu-linux-project")

---

### Post by chewearn on 2007-03-07
I would suggest you use Windows Disc Management tool to check if all is in order.  I think you should see Windows partition now taking up the first 20GB of the disk, the remaining is empty unpartitioned space (note: if Windows pops up a wizard to initialise the disk, click [Cancel]).

Then try ubuntu installation again, but this time choose option 2 "Use largest continuous empty space", or something like that.

---

### Post by Mydree on 2007-03-07
Thanks! Where is this Windows Disc Management? I looked on my system and don't see it. (I apologize, I'm not a regular user of Windows.).

---

### Post by Mydree on 2007-03-07
[How to use Disk Management to configure basic disks in Windows X]("http://support.microsoft.com/kb/309000")P

---

### Post by Mydree on 2007-03-09
It worked, thanks!

The Windows Disc Manager (WDM) is a Windows application. I was afraid by going Start> Run> application that I would be in MS-DOS or something. Anyway, in WDM it was easy to click on Disc Management and it was easy to that Windows was the primary partition.

---

### Post by chewearn on 2007-03-10
Glad to be of help.:)

---

