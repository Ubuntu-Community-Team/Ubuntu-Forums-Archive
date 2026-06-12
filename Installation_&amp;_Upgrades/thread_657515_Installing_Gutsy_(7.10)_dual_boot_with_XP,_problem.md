---
title: "Installing Gutsy (7.10) dual boot with XP, problems creating partitions"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by jvandijck on 2008-01-03
I am in the process of editing the partitions (step 4 in the installation process): everything went fine reducing the size of the ntfs windows partition (from 193 to 95 GB). Then creating the root partition (10GB) went well. Then I wanted to edit the free space to create the swap partition: the swap partition itself is created, but the "free space" now turned into "unusable space". So, I cannot edit this to create the home partition...
Note: I would have expected to see a device called /dev/sda, the only device shown is /dev/sde.

---

### Post by Pumalite on 2008-01-03
Post your specs. Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it and tell me what you see or post a screenshot.

---

### Post by pietjanjaap on 2008-01-03
reboot

---

### Post by jvandijck on 2008-01-03
See two pictures, moving from picture 1618 to 1619 you see the free space turning into "onbruikb " (dutch for unusable).

---

### Post by dretep on 2008-01-03
Could it be you have unusable space due to you making the first 4 partitions primary?

---

### Post by jvandijck on 2008-01-03
I have rebooted, still the same problem: once the swap partition is created, the free spaces turns unusable...

---

### Post by dretep on 2008-01-04
Before you create the 3rd partition, created a logical partition, don't make it a primary.  Then create your 10GB root partition and swap partition in that logical partition and you will still have all the remaining space available.

---

### Post by Pumalite on 2008-01-04
+1

---

### Post by jvandijck on 2008-01-04
This one can be closed, not sure how to do...I have followed dreteps advice and all works well now. Indeed, a master boot record can only have a max of 4 primary partitions. If you need more, you need to work with logical partitions (as I also found on Wikipedia). THANKS TO ALL  :):)

---

