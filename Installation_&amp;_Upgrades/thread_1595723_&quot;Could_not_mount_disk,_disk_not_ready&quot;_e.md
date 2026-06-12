---
title: "&quot;Could not mount disk, disk not ready&quot; error since 10.04 to 10.10 upgrade"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Rat2000 on 2010-10-13
Since I've upgraded to 10.10, when I boot Ubuntu I get a message during the splash screen. I claims that it can't mount one of my disk because it isn't ready and asks me to either wait, skip by pressing "S" or manually solve the issue by pressing "M".


It's the first time I see this so I skip. It asks me again for all my secondary drives, except the one I have to boot into Windows (which is the boot drive).

Once booted, I have no issue mounting the drives. Except the first time where I had to delete their /media/[mountpoint] folders because they where mounting on /media/[mountpoint]_.

I ran the NTFS tool (some of the disks are NTFS, some are Ext3), I ran the disk utility to make sure they are properly configured but on next reboot I'm still told the disks can't be mounted at boot and whether to skip mounting them.

Thanks for any help.

---

### Post by Rat2000 on 2010-10-18
I've tried everything. I have no issue mounting the drives once I've logged in and using the Disk Utility tool. The problem is next time I reboot I have to start over.

---

