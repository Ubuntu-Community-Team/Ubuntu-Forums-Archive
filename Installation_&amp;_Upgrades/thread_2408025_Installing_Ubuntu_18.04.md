---
title: "Installing Ubuntu 18.04"
date: 2018-12-12
forum: Installation &amp; Upgrades
---

### Post by Bob_Younkin on 2018-12-12
I have a new Dell 5000 that I am trying to install Ubuntu 18.04 on.
I freed up 320GB of space for Ubuntu and expected Ubuntu to do its thing, but I got an error message that I needed to partition this free space before I could install Ubuntu.  I screwed up the partition.  It failed.  After a couple of more tries, the free space I created is one labelled "Unallocated" space and is not available for Ubuntu installation.  I tried restoring the Win partition and then shrinking it again, but the space is still labeled unallocated.

Thoughts on how to get the free space back?

Bob

---

### Post by oldfred on 2018-12-12
UEFI or BIOS system and are you dual booting with Windows?
Post this:
sudo parted -l

UEFI uses gpt partitioning and BIOS uses MBR partitioning with its 4 primary partition limit. 
New systems in last 5 years are all UEFI with gpt partitioning, unless user converts it.

Dell typically needs UEFI update from Dell and if SSD, firmware update for SSD.
And drives need to be AHCI mode, not RAID, nor Intel SRT.

       Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)
Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889) 
    
General UEFI install info in link below in my signature.

---

