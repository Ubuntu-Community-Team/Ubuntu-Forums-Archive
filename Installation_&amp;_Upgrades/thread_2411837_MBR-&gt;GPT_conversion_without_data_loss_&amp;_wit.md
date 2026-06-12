---
title: "MBR-&gt;GPT conversion without data loss &amp; with live CD"
date: 2019-02-04
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2019-02-04
I've got a MBR formatted HDD that I use in an external enclosure as storage for now. I'm going to put it in a desktop PC to use it as the only PC's HDD, then I'll install Win10 and Ubuntu in dual boot, therefore I've to convert MBR to GPT for 1st and I hope to get that without data loss because I'd be in trouble to do a back-up due to the fact that I've got not enough optical discs for the total amount of data on the HDD.
There's one more problem to that. I've no ubuntu distributions installed so I'll have to manage all that from a live CD. I've got an old Lubuntu 12.04 CD and I guess I can use only that because I've got only a very old notebook to do this job with very low cpu and ram (1.25GB) power.

That's my situation with all its limitations and goals. Is that possibile? Is there a way to be sure not to lose data doing that?

---

### Post by oldfred on 2019-02-04
You should not attempt this without backups.

I may be possible to convert, but then you do not have required partitions for Windows, nor Ubuntu.
Windows has to have these partitions, note difference between UEFI/gpt  & BIOS/MBR.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
Ubuntu will only need an ESP which is shared with Windows and / (root) as ext4 partition. But most use a smaller root and either larger /home or data partition(s).

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

