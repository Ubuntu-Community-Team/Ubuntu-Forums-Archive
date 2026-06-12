---
title: "XP and Ubuntu with nVidia RAID"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by rc2k7 on 2007-03-04
I need some help installing Ubuntu on my home computer. I am new to Linux but I do have a little practice with Ubuntu because I had installed it on a test machine. I am now wanting to install it on my main computer. I do work on Windows computers for a living so I am not afraid to get my hands dirty. Here is my situation.

I have 4 hard drives on my computer. 2-80GB SATA hard drives set to a RAID 0 that has my XP install on it, 1-250GB IDE drive that is for storage and 1-320GB SATA that has 2 partitions on it, a 220GB for more Windows storage and 100GB part that I want to be able to install Ubuntu on.

I have already attempted to install Ubuntu on this computer but aborted when I saw that Ubuntu did not recognize my RAID setup.

I am hoping for a dual option that will keep my RAID 0 intact to boot into Windows.

Thanks for any help in advance.

---

### Post by nyinge on 2007-03-05
AFAIK, software raid support hasn't been implemented properly on Ubuntu, but it's possible.  Yes, you'll get your hands really dirty here.  :P

[FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto") is a great guide that had helped me run my system successfully.  Even though you're installing Ubuntu to a non raided drive, the boot loader must still recognize your XP on raided drives to be able to boot both OS's.

Please also note that the guide is intended for installation of both Windows and Ubuntu on raided drives.  There's a bit of difference between the guide's setup and yours, but I believe it's adaptable.

Take EXTREME CAUTION when you're performing the steps in the guide, as one crucial mistake could easily turn your data into oblivion.  I'd suggest you read though the page at least twice before actually starting.  Good luck!

---

