---
title: "Dual booting on a desktop."
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by Extol11 on 2013-05-02
HI! I am about to wipeout a windows installation because it is on a 1TB hard disk drive that I'd rather use for storage. I'm moving Windows and Ubuntu into 500GB instead so I have the spare third hard drive for a third computer I'm planning to build. I would like to know if this could affect performance of either OS (as far as speed goes) and if there's something I should know before I do it. I know windows can only be installed in a primary partition and in the first partition. These are not SSD and I suppose putting Ubuntu as close to the end of the hard drive will make it be faster since the hard drive will cover more area in less time. The main purpose for these two OSs is gaiming since I do programming on my laptop. Am I better off leaving each os in a separate HDD or should I dual boot?

---

### Post by oldfred on 2013-05-02
With multiple drives I prefer Windows on one and Ubuntu on all the others. But if you want to dual boot you can. Order on drive is not critical. It can be any primary partition, but I think a few users that put a  primary at the end of a drive or had extended before the Windows had  partition table issues. Windows may rewrite partition table and not see Linux partitions so it does not write partition table correctly. You can use sfdisk to make a partition table backup just in case (only if MBR not gpt).

Windows will boot from a NTFS formatted primary partition with the boot flag. If the NTFS partition is created in advance Windows 7 will install into one partition not the normal two. 

 Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by Extol11 on 2013-05-02
Ok. Just one more questions. Is Lubuntu 13.04 having any problem at all with Steam? I am using 12.10 and valve games don't want to run. I was thinking of going back to 12.04 since (while it is not a LTS version) it should be more stable or ironed out. The pictures viewer had a problem in 12.10 where viewing pictures would be messed up once you installed ATI's official drivers. And there were some rough edges with it where the gui would crash for no apparent reason and go straight back into working. It it no show-stopper but still a bit annoying.

---

### Post by oldfred on 2013-05-02
I do not know anything about games.

But I get the idea that it is like Windows, you need a high end system with good video card. One good thing about games in Linux is that the Video vendors are all updating drivers.
But you only get the newest kernel & newest drivers with the new versions of Ubuntu.

---

### Post by Extol11 on 2013-05-02
> **oldfred said:**
> I do not know anything about games.

But I get the idea that it is like Windows, you need a high end system with good video card. One good thing about games in Linux is that the Video vendors are all updating drivers.
But you only get the newest kernel & newest drivers with the new versions of Ubuntu.

I'll give Lubuntu 13.04 a try. If anything goes wrong I'll just install 12.04 over it. Thanks for all the help.

---

