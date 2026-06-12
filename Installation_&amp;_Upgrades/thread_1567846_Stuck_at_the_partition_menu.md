---
title: "Stuck at the partition menu"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Slim1950 on 2010-09-04
I tried installing on a Win 7(64 bit) machine. The install procedure gets to the partition menu, and there it stays. all my menu options are dimmed out and I have the choice to cancel move forward or back up. Moving forward gives me the error, "Root menu not defined.." or something like that..

Can anyone help? It has created a mutliple boot system though.. so now I can choose.. it must have installed via a live session I did prior with the cd..

---

### Post by oldfred on 2010-09-04
Have you used all the primary partitions?

From the liveCd. so we can see what partitions you have.

```
sudo fdisk -lu
```

---

### Post by Slim1950 on 2010-09-04
> **oldfred said:**
> Have you used all the primary partitions?

From the liveCd. so we can see what partitions you have.

```
sudo fdisk -lu
```

Thanks.. I deleted my entire Win7 Hard Drive and did a complete install.. everything works now. Ubunut did not want to install otherwise, it seems. I probably overlooked something.

---

### Post by -kg- on 2010-09-04
Yes, likely you ran up against the "4 Primary Partition" limit.

Since you deleted your Win 7 partition and made no bones about it, I guess you're fine, but you could possibly have made the installation without doing that.  What you would have needed to do is eliminate one of the Primary partitions (other than your Win 7 partition) and created an Extended partition.

An Extended partition is a special type of Primary partition in which you can create many partitions, called Logical partitions.  Windows (generally) must be booted from a Primary partition, but Linux can boot from a Logical partition, as well.

For a "next time" scenario, you might want to read at the "How To Partition" tutorial linked to in my signature block.  It will give you basic knowledge on hard drives and partitioning operations.

---

