---
title: "Dual boot error (Ubuntu not recognizing partitions)"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by cyriacd on 2014-02-17
I want to dual boot windows 8 and Ubuntu 12.04. I installed windows 8 first as recommended by most posts. Then I allocated space for Ubuntu and left it unformatted. So then now there is an empty partition (504GB) along with the windows partitions (about 496GB). But when I use try to install Ubuntu , it first doesn't recognize the windows installation, and when I choose something else, There is one partition with free space.(about 1000GB). Is there anyway that I can solve this issue and dual boot windows 8 and ubuntu12.04? Thanks to anyone who is willing to help.

---

### Post by oldfred on 2014-02-17
If you installed yourself, did you install in the 35 year old BIOS mode or the new UEFI mode? If an older computer it will not have UEFI, but new UEFI systems have both. And both installs need to be the same boot mode.

And whether UEFI or BIOS you must turn off the fast boot or always on hibernation. The Linux NTFS driver will not mount so NTFS not seen if hibernated or needs chkdsk.

There are several other possibilities, drive previously gpt, RAID data on drive. And others.
       Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

