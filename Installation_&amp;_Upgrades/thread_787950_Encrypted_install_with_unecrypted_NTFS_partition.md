---
title: "Encrypted install with unecrypted NTFS partition"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by allaboutsam on 2008-05-09
Hi all,

I need to set up a hard drive with an encrypted 8.04 installation (like the one created by running "use entire disk and set up encrypted LVM") *plus* a separate small unencrypted NTFS partition.

Can the alternate installation CD create an NTFS partition on a blank hard drive?

If yes, I assume I will have to do it manually. Can anyone point me to an explanation of how I want to set up the 8.04 part of it to match what is created by the "use entire disk..." option--but without using the entire disk?

If not, can gparted be used after installation to resize the encrypted partition? Or will that damage it?

Many thanks in advance,
allaboutsam

---

### Post by sanjeevpunj on 2008-05-09
I ran into this problem too. I used the guided partitioning method and what happened was that my WindowsXP Partition got downsized to just 20GB and Ubuntu took up remaining 950GB (in a 1 TB HDD). Some other smaller partitions (which i created just to store crucial data using Western Digital's Data Lifeguard Tools) occupy the remaining space, while some space is saved in some hidden partition too. I now want to resize the 950GB Partition, and limit the UBUNTU OS to half of it, so that I can save my work in Windows XP ona decent sized partition without having to worry for diskspace. What Ubuntu has done is just claim unused space and format it with the EXT3 Filesystem.

---

