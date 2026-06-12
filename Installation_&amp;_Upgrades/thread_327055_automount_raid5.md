---
title: "automount raid5"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by vdhagen on 2006-12-28
Hi,
a relative newbie to ubuntu I created a raid5 array which is accessible from windows (and has already several GB of content).

Right now I still have to mount /dev/md0 manually. I probably should insert
/dev/md0       /mnt/nas             ext2     defaults        0       0
into /etc/fstab. Could anybody confirm this?

So far I haven't been able to find out the format of the fstab lines (some examples use "defaults 0 1" others "defaults 1 1"). Could somebody provide me with an address where to look? Thanks.

Oskar von dem Hagen

---

### Post by pay on 2006-12-28
> **vdhagen said:**
> /dev/md0       /mnt/nas             ext2     defaults        0       0
into /etc/fstab. Could anybody confirm this?That should work fine. The fifth column is for dump options and the sixth column is for file system check.

---

### Post by vdhagen on 2006-12-29
Included "/dev/md0        /mnt/nas          defaults 0 0" into /etc/fstab. No improvement. :-(

The idea is to use the computer as NAS without monitor adn keyboard. Right now I still have to manually mount /dev/md0 manually via ssh.

Any idea what could be wrong?

Oskar von dem Hagen

P.S. Do I have to umount the /mnt/nas before shutdown?

---

