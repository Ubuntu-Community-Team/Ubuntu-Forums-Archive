---
title: "Cannot install Feisty using mdadm"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by matt_b on 2007-07-22
I am trying to install Feisty on my Shuttle SB81P box that has two 120GB Maxtor SATA drives. I am using the alternate install CD (i386), and when prompted with the partitioning screen I create my partitions, RAID1 them up and proceed. It gets all the way through to "select and install software" where it hangs at 6%, then gives me a red "install failed" screen. I rebooted and next time it got to 18% then hung for an hour without moving. If I install without RAID (i.e. pick guided partitioning - use entire disk) the install completes without error.

Can anyone shed some light as to why the install works without mdadm but not with?

Thanks
matt

---

### Post by matt_b on 2007-07-24
I've tried using the Dapper alternate CD and it installs without error - it's just Feisty that won't install with RAID.

Any ideas anyone..?

---

### Post by Circuit99 on 2007-07-24
I have a question are the hard drive properly setup they have to be capped if the motherboard does not support SATA II. The other is manual configure your partitions.  Setup raid then see if gparted recognizes the hard drive as whole hard drive.


Hope this helps

---

