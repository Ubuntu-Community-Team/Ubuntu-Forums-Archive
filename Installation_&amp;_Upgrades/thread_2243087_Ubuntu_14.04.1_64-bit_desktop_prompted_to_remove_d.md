---
title: "Ubuntu 14.04.1 64-bit desktop prompted to remove disk halfway through install"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by ESwin33 on 2014-09-06
Hi everyone, 

I am trying to install Ubuntu 14.04.1 64-bit on my HP 2000 Notebook PC alongside Windows 7, however when I choose to install "Inside Windows 7" during installation it prompts me to remove the disk and press enter. After doing this my computer restarts with no visible changes. I am using a Rewritable CD for this. I have burned the image onto the CD and checked it through the installation process. It says the disk is OK, but it still doesn't work. If it helps, my computer has 3GB RAM and 177GB of Hard Drive Space left.


Thanks in advance for any help.

---

### Post by ubfan1 on 2014-09-06
Read the stick note at the top of the messages titled: 
[h=3][Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")[/h]

---

### Post by hakuna_matata on 2014-09-07
> **ESwin33 said:**
> however when I choose to install "Inside Windows 7" during installation it prompts me to remove the disk and press enter.
If you see the option "inside Windows" instead of "alongside Windows", your partitions of your hard disk are not useable for Ubuntu Installer. Reasons could be 4 Primary partitions or Dynamic Disks.

Primary partitions: [https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)
Dynamic Disks:[http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785%28v=vs.85%29.aspx)

---

