---
title: "New user of ubuntu: Creating Partitions for installing"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by ArrAld on 2007-03-31
:confused: Hello...

I'm installing ubuntu in my desktop...and I had some troubles runnig the live cd (both 6.06 and 6.10, eventhough the cd was well burned) SO I discovered that that problem could be solved by running first the gparted and creating the partitions before running the live cd of ubuntu. So I did that and create the partitions (besides and extra one I had before for windows in FAT32). The gparted gave them, for default (I mean I had no other alternative to chose) the status of primary partitions for the 3 of them: 1ª for linux in ext3; 2ª swap, and the last one, 3ª for my documents in FAT 32.

SOme days ago I tried to make the partitions with Partition Magic, and I had some troubles (first the xmnt2002 error; and then the autochk.exe not found"....I've read in somo forums that the problem was for having more than one primary partition, because windows in a confusion hide the partitions and cannot found the autochk.exe file eventhough I actually had it in my computer and in the file it was supoosed to be that windows was not able to find.

So my question: should I convert all these three partitions in logical (but I would have to use the partition magic, in which I have not many confidence)¿??¿

In where I'm supposed to mount my partition for windows without risking losing my information in that partition??¿

---

### Post by mikewhatever on 2007-03-31
The rule I know of is, you can't have more then 4 primary partitions on an HDD. If all of your existing partitions are primary and you need another one, then yes, you should make at least one of them extended, so that you can create more logical ones. Windows is usually mounted in /media/hda1, but it does not really matter. A mount point does not loose you any data.

---

