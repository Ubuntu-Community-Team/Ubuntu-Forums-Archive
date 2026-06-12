---
title: "Mythbuntu 9.10 Install on Dell 670 SCSI drives"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by louv on 2009-11-24
I have a Dell 670 with multiple scsi drives, non-RAID config'd. The liveCD for Mythbuntu 9.10 fails to find disks to install at the partition disk step. There are no available disks or partitions recognized in that installer step. 
Quiting the install, brings you to the desktop environment. Using a terminal, the devices are recognized as sda & sdb, and can be mounted, and used. The use of the drives is normal in this desktop. Trying the desktop installer icon again starts the installer with the same partitioner step outcome.

Are there start-up options which can be added to aid in recognizing these drives?

I have added the option, rootdelay = 90 as one ttempt without success.
I have checked the MD5SUM, etc.

---

### Post by jjcv on 2009-11-24
I suspect the driver for your SCSI disks/card may not be on the install disk you are using.  

Have you tried booting of the Alternative Unbuntu install disk to see if that finds the disks?

---

### Post by louv on 2009-12-01
Thanks for the reply. It is not scsi drivers, exactly. I finally found the procedure after submitting this question.

Here is a short summary of what I found.

The raid controller although not utilised, it is still being assumed functional by the installer.

Run the LiveCD and specify 'nodmraid' in the options <F6> AND wait for it to fail and go to the desktop, THEN remove dmraid with apt-get, THEN install from the icon on the desktop.

Two URL which were my leads:
[http://ubuntuforums.org/showthread.php?t=1329650&page=2](http://ubuntuforums.org/showthread.php?t=1329650&page=2)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8220529](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8220529)

Thanks for the reply, I had initially searched in vain but eventually came upon the exact recipe. 

Problem Solved.

---

