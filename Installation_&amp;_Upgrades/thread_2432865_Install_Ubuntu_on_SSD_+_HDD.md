---
title: "Install Ubuntu on SSD + HDD"
date: 2019-12-10
forum: Installation &amp; Upgrades
---

### Post by adynouni on 2019-12-10
Hello!
I would like to install Ubuntu 18.04 on an Acer Aspire 3 laptop.
Data: 4 GB of RAM, 128 GB SSD and 500 GB HDD.
Please tell me how to partition the drives correctly?





I have a similar situation on my hands, considering to take out a loan. I forgot about a big bill that was drawn last Friday and put all my buffer on the depot which takes days to redeem (stupid). I am going on an important seminar trip this week. IF I do not receive cash before then the least stupid fast loan of about $300. I found this offer ([full text]("https://www.wisconsinpaydayloans-wi.com/") here). Will update you on how it went. PS: I have no bad credit history, so really counting on a good interest rate.

---

### Post by oldfred on 2019-12-10
Partitioning is unique to each user and what he wants to do.
Also if new user default install is easiest, but that just puts / (root) on drive you select. You can then create partition(s) and mount them as data partitions.
But for a new user often easier to have / on SSD and /home on HDD.

Acer also has some unique requirements. You have to enable "trust" after install.
Acer also requires UEFI update as some versions of UEFI, left off the way to set "trust".

With UEFI you also must have an ESP as first partition on SSD. Use gpt partitioning, not old MBR partitioning. Ubuntu now uses swap file, so swap partition, not now required. Older instructions may still suggest swap partition.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            UEFI/gpt partitioning in Advance, new versions do not need swap partition:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) &
[URL="https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation

      [/URL]
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[URL="https://ubuntuforums.org/showthread.php?t=2358003"]https://ubuntuforums.org/showthread.php?t=2358003

      [/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

       Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)

For more UEFI install info, see link in my signature below.

---

