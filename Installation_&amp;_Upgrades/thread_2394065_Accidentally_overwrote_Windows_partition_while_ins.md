---
title: "Accidentally overwrote Windows partition while installing Ubuntu"
date: 2018-06-12
forum: Installation &amp; Upgrades
---

### Post by hongj77 on 2018-06-12
Hi everyone. While trying to install Ubuntu 14.04, I've accidentally overwritten the original Windows partition on my Alienware laptop :(
Now, I'm trying to undo the mistake and reinstall Windows, but I'm finding it to be a difficult task because I cannot access the Windows recovery partition since my computer always boots up in Ubuntu.
Has anyone encountered similar threads dealing with this issue? Or have any links to resources? Any information would be of help, I'm not sure where to start.
Thanks.

---

### Post by Impavidus on 2018-06-12
Do you have to rescue any documents from that hard drive? In that case, don't boot your installed Ubuntu system and look into file recovery. Chances are you can rescue most of your documents, but it may be a tedious job to sort everything out.

If your documents are safe, run in a terminal```
sudo parted -l
```That should show us the partitions present on your hard drive. Chances are you not only wiped the Windows C partition, but the recovery partition too. You may need a full Windows install disk.

Besides, why Ubuntu 14.04? Two more recent long term support releases are available, 14.04 has less than a year of support left.

---

