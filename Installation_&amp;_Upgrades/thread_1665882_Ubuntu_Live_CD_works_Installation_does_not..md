---
title: "Ubuntu Live CD works Installation does not."
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by TehPeanut on 2011-01-12
Hey guys im new to Linux and im exspreriencing a few problem that I would love to get fixed before I go to sleep

Ill give a quick rundown on whats happend
Create Ubuntu boot CD
Windows 7 64bit corrupts
WinXP install corrupts
Attempt to install Ubuntu 10.10 fails (error 5)

The live CD works fine I get about 3 quarters in of copying files and then it stops
I currently have no OS on my computer and this is the only CD that works
Im useing my brother laptop and ive attempted 5 times to burn a new disk useing CD-Rs and multiple burning software but all disks come out blank.
(Im currently re-downloading the 32bit image)

My bios are set to auto
I have no idea how to fix this so any help at all would be appreciated


My specs:

Advent
Intel coreDUO Quad
4gb RAM
Nvdia GForce (not sure which Model)


Thanks

---

### Post by tommcd on 2011-01-13
> **TehPeanut said:**
> 
Windows 7 64bit corrupts
WinXP install corrupts
Attempt to install Ubuntu 10.10 fails (error 5)
If everything is getting corrupted, this sounds like a faulty hard drive, or perhaps faulty memory. You should rule out a hardware problem here. Run memtest for at least a few hours from the Ubuntu live CD. Also, try using the hard drive test utility provided by the manufacturer of your hard drive to make sure the drive is ok? How old is the hard drive you are using?
> **TehPeanut said:**
> 
The live CD works fine I get about 3 quarters in of copying files and then it stops

Be sure to check the **md5sum** of the Ubuntu iso image you downloaded: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also, when you boot the Ubuntu live CD be sure to run the option to *Check CD for Defects*: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
Be sure to burn the CD at the slowest possible speed. If you are burning the Ubuntu CD from Windows, try using Iso Recorder or Infra Recorder: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Write back if you need more help.
And welcome to the Ubuntu forums!

---

