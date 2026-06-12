---
title: "Incorrectly partitioned hard drive"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by arah91 on 2008-07-25
So i recently installed a version of ubuntu ,and i portioned it wrong (i think that is the word at least) the problem is that it is a 110 GB hard drive but now i only have 10 GB to work with the rest is being used in ubuntu. I tried hooking it up to a different computer and formatting it but i still just have 10 GP and would really like to get some more space. Thank you any help is greatly appreciated

---

### Post by EXCiD3 on 2008-07-25
Use the manual partitioning when you setup your Ubuntu installation, do at least 10GB for Ubuntu, twice the size of your ram for Swap, and use the rest at your discretion.

The easiest way to fix your issue is to just put in the livecd, boot into it and then go to System-Administration-Partition Editor and resize your partitions, first shrink the big one and then increase the size of the 10GB partition.

---

### Post by arah91 on 2008-07-26
hey i would like to thank you for the help i have fixed the problem i was also dual booting with windows vista and was able to fix it through there OS i wen to control panel -> system and maintenance -> administrative tools -> computer management -> storage and in there i was able to format the partion that was 100gp then i booted up linux in the 10gb partion i mentioned earlier

---

### Post by Sef on 2008-07-26
> Use the manual partitioning when you setup your Ubuntu installation, do at least 10GB for Ubuntu, twice the size of your ram for Swap, and use the rest at your discretion.

The swap advice is not quite correct.  If you have swap of 1 GB or more then 1 GB swap is the most you should have if you use it at all.

---

