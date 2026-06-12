---
title: "mdadm RAID5 volume &amp; dead system drive"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by zylithi on 2010-01-17
I have a server with the following setup:

Kubuntu 7.10
4x500GB hard drives, 3 in RAID5 configuration via mdadm, 1 O/S drive

Last week, the system drive flat-out died; not surprising considering its been under heavy load for 2 years.

Problem I have, is I'm sort of worried about reinstalling the operating system, while somehow retaining all the old data from the RAID5 volume. Does anybody know if it's possible that the system will automatically recognize the RAID5 volume and automatically work with it, or will i have to do plenty of legwork?

The drive structure is structured as follows:

/dev/sda is system drive
/dev/sdb --.
/dev/sdc -----> RAID5 volume
/dev/sdd --'

I'm not using any kind of fancy UUIDs to reference the drives because... to be honest, I have no idea how they work. -.- Am I SOL here, or is there a way to use mdadm to import old drive data?

---

