---
title: "What shall I select when asked to partition."
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by KuifjePDX on 2008-07-09
I am trying to upgrade my Edubuntu 6.06 to the new 8.04.1 desktop. I booted the Live CD and from the Ubuntu desktop I run Install.

Page 4 of 7 deals with partitioning. The current setup is:

/sda1 swap (1011MB)
/sda2 FAT32 (21000MB) for Windows98 (yes, I still need that to run ONE program)
/sda3 NTFS (21000MB) for WinXP Home SP3
/sda4 ext3 (31000MB) for Edubuntu

So the partitioner recognizes these partitions. I double clicked the swap partition but there are no options to choose there, other than swap. For the ext3 partition I chose ext3 again, checked the Format box, and selected / as mounting point.

Now the two Windows partitions is where I have a question. Do I just leave them as shown? Or should I edit each one? The drop-down list doesn't offer NTFS anymore (as far as I could see) but a couple other FS's that I am not familiar with. It does show a FAT32 type as well.

Or should I use the Do Not Use This Partition option for both Windows partitions? I'm afraid to commit as the final warning said something along the lines "All Data Will Be Lost, Even For Those Partitions Not Used".

So...please help guide me for the best selection. I don't want to loose the data on the Windows partitions.

Thanks!

George

PS. I am somewhat computer literate.

---

### Post by mikewhatever on 2008-07-09
First, it looks like you are not upgrading, but reinstalling. The major difference is that you'll loose all data on the / partition because it will be formatted.
All you may want for ntfs and fat32 partitions are mount points. If there is no such option, choose the 'do not use' one. You don't need to specify it is ntfs since it's already recognized as such.

---

### Post by KuifjePDX on 2008-07-09
Hi Mike,

Thanks. You are right, I am reinstalling. To me it's an upgrade from 6.06 to 8.04.1 but the process I'm using is installing the new one right over the top of the old one.

I was scared off by the warning on the last page (7 of 7) of the Ubuntu installer that warns about loosing data on all partitioned selected for formatting AND those selected not to be used (or something worded along those lines). I don't mind loosing the data on hte old 6.06 partition(s) (swap and /) but I'd like to keep the data on the two Windows partitions as they are a bear to recreate/reinstall.

SO, if I understand your response right, I should just use the "Do Not Use" option for the two Windows partitions and the Ubuntu installer will leave them alone and not mess up their partition table entries.

Unfortunately, I don't have a system to just experiment on. Therefore, I'd like to be absolutely clear on what will happen to those two Windows partitions.

Thank you.

George

---

### Post by mikewhatever on 2008-07-09
Yes, that's correct. You'll still be able to access those partitions through Nautilus' side panel after the installation.

---

