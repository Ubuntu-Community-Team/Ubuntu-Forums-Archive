---
title: "Partition Names Changes?"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by jakenn-linux on 2007-07-02
I'm ready to upgrade from 6.06 to a clean install of 7.04.  I have current partitions:
hda1 through hada3 (primary) and hda4 (extended).  Hda3 is my WinXP partition (I multi boot and in my extended partition I have my sway and a FAT32 shared partition.  I need to delete hda1 (Ubuntu 6.06) and hda2 (SuSE 10) so that I can create new partitions for Ubuntu root (hda1) and /home (hda2).

BUT, when I go to GPartEd on the liveCD (or the partition step in the installation), I find my partitions now have a different name: hda1 is now sda1, hda2 is now sda2 and so on.  On the choosing partitioning method page it also seems to say my IDE hard drive is now a SCSI.

Will this be a problem, or can I just continue with the process of deleting hda1/hda2 (which is now called sda1/sda2) and creating free space and then two new partitions and not worry about hda/sda?

Thanks.  I don't remember this happening when I did a clean install on my laptop.


LATER ADDITION:  Someone just told me that beginning with 7.04, ALL drive/partitions are now sda instead of IDE being hda and SCSI/USB drives being the sda.  Didn't see this in any of the partition helps.  IF this isn't true, please let me know before I mess up my clean install.

---

