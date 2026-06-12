---
title: "won't boot after yesterday's kernel update 10.04 LTS"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by biosol on 2012-06-14
After yesterday's update of my Ubuntu 64 bit 10.04 LTS OS that runs off an external USB3 drive (enclosure), the system won't boot.  It stalls at the GRUB prompt.

GRUB>_

It looks like it says lubuntu grub 1.98 if my memory is correct.


I have booted from a USB drive and see that the drive has two partitions, sdb1 is the root and boot partition.

I have tried this command from a USB live CD, but it didn't work.

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

Can someone help get me back up and running?

---

### Post by biosol on 2012-06-14
Anyone have any ideas?

---

