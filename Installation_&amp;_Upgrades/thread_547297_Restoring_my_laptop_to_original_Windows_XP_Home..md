---
title: "Restoring my laptop to original Windows XP Home."
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Tzustrategy on 2007-09-09
Hey folks!

Well, it sure seems like luck is on my side. I've been happily using Ubuntu for two months now, and have essentially made the complete switch. I love the ease of use and stability. However, the laptop I currently have isn't supported by Compiz Fusion, leaving me out in the cold when it comes to awesome window management. 

Here's where my luck comes in. It turns out my mom is buying a laptop in a few days very similar to mine, but instead of choosing the AMD/SiS configuration I have, she's choosing a rig with a Core 2 Duo/GMA graphics card. As this is supported by Compiz Fusion, I'm taking a keen interest. As my mom is going to be a Windows user due to some industry specific software she uses, I've offered to trade my laptop for hers. I get the Intel chipset laptop, throw on Ubuntu with Compiz Fusion, and am happy.

The only stipulation here is I have to restore my laptop to its' original settings (Read: Windows XP Home). The original set up was two FAT32 partitions. I burned the recovery CD the Acer recovery software suggested I do, but I have a few questions.

1) Will my current dual partition setup adversely affect the restore to original factory settings?
50GB  ext3 Ubuntu partition, and a 50GB FAT32 Windows XP Home partition. 

2) If it would adversely affect the complete restoration, I would have to delete Ubuntu. This being the case, would a simple delete of the Ubuntu partition and Linux swap be sufficient to get me back to an all windows machine, or would I need a Windows installation cd to run the "fixmbr" command?


Thanks so much in advance for all your help! :)

---

### Post by Pumalite on 2007-09-09
I think #2 is correct. Remember I'm not a Windows user, but deleting Ubuntu , expanding partition and fixing Windows MBR with CD sound OK to me.

---

### Post by oilchangeguy on 2007-09-09
the recovery cd should only use the 50 gb windows partition you presently have. if you want to keep ubuntu, you'll need to restore grub, after you install windows.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by carusoswi on 2007-09-09
I think you will find that you need to restore the disc to its original configuration before running the PC specific restore discs.  I once needed to restore a Compaq desktop.  The only disc alteration I had made was to use Partition Magic to add and resize some partitions.

The restore disc tried to run, but would stall at one point during the process.

Setting the partitions back to their original (one large partition) fixed the problem.

A full install of XP may or may not work, but, I'm guessing that restore discs will choke on the non-fat32 partitions.

You could, of course, just edit the GRUB so that XP is first in the default boot order.  Your mom may not know the difference.

Caruso

> **Tzustrategy said:**
> Hey folks!

Well, it sure seems like luck is on my side. I've been happily using Ubuntu for two months now, and have essentially made the complete switch. I love the ease of use and stability. However, the laptop I currently have isn't supported by Compiz Fusion, leaving me out in the cold when it comes to awesome window management. 

Here's where my luck comes in. It turns out my mom is buying a laptop in a few days very similar to mine, but instead of choosing the AMD/SiS configuration I have, she's choosing a rig with a Core 2 Duo/GMA graphics card. As this is supported by Compiz Fusion, I'm taking a keep interest. As my mom is going to be a Windows user due to some industry specific software she uses, I've offered to trade my laptop for hers. I get the Intel chipset laptop, throw on Ubuntu with Compiz Fusion, and am happy.

The only stipulation here is I have to restore my laptop to its' original settings (Read: Windows XP Home). The original set up was two FAT32 partitions. I burned the recovery CD the Acer recovery software suggested I do, but I have a few questions.

1) Will my current dual partition setup adversely affect the restore to original factory settings?
50GB  ext3 Ubuntu partition, and a 50GB FAT32 Windows XP Home partition. 

2) If it would adversely affect the complete restoration, I would have to delete Ubuntu. This being the case, would a simple delete of the Ubuntu partition and Linux swap be sufficient to get me back to an all windows machine, or would I need a Windows installation cd to run the "fixmbr" command?


Thanks so much in advance for all your help! :)

---

