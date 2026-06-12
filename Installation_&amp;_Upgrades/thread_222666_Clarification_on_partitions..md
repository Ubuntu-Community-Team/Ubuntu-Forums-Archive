---
title: "Clarification on partitions."
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Omegabf on 2006-07-25
I'm considering added Ubuntu, but there's a few things I want to check before hand, which the tutorial doesn't seem to give a clear answer to:

* Is the partitioning non-destructive?  (i.e. will it probably leave my windows install working & the data intact?)

* Can I make sure that the new parition does not cause windows to change the drive letters on the CD/DVD drives?

* Is there a way to place my files so that I can easily access them from both Windows and Ubuntu?

---

### Post by philippe_carlo on 2006-07-25
(1) Ubuntu will not destroy windows partitions unless you tell it to.
(2) Keeping your linux partitions 'behind' the windows ones is good practice. However, windows will not recognize the new partitions, so they do not influence drive letter numbering. Be carefull with the Windows partition manager (don't use it), because it tends to behave Linux-unfriendly, read: kills Linux partitions without mercy.
(3) You can have one 'common' FAT32 partition. These are writable for both Linux and Windows. NTFS is only readable in Linux and Linux partitions CAN be accessed in Windows using special tools. So, I guess you're fine.

---

### Post by Omegabf on 2006-07-25
Great.  Thanks for the help.

---

