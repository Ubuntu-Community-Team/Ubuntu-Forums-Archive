---
title: "Help suggest appropriate partitioning"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by williamblue on 2010-06-09
Please forgive me if this isn't in the appropriate area.  I haven't ever initiated a thread before.

I just purchased a new MSI WindTop AE2220 with a 320 GB hard drive running Windows 7.  I want to dual boot until I know I have found all of the appropriate drivers.

The confusing part is that the computer came with 4 partitions as displayed in the attached screenshot jpeg.

How would you recommend I resize and partition my drive?

Current Partitions (in order):
Recovery Partition 14.65GB / 14.45 free
Active Recovery 100 mb / 100 mb free
OS-Install (c) 68.36GB / 42.06 GB free
Data (D) 214 GB / 213 free

Will install Lucid 10.04

---

### Post by darkod on 2010-06-09
Have you decided how much space you want to give to ubuntu?

---

### Post by ajgreeny on 2010-06-09
As there is a nice big data partition already which is almost, if not totally empty of any important files, you could simply delete that partition and make a new extended partition in that space.  In that extended partition make a new logical partition for data, again as ntfs, but leave about 20 GB for ubuntu and install ubuntu to that 20GB as logical partitions.  I suggest 10GB for root, 2 - 4 as swap and the the rest for a separate home.  Make sure your Documents and music, photos, videos etc etc are all saved by ubuntu into the data partition, which you should mount at boot by using ntfs-config and ntfs-3g, which you may need to install first.

Others will undoubtedly give you many different answers and will make you more confused, and I accept that this is just one recommendation, but it is what I would do if I had any windows install to worry about.

---

