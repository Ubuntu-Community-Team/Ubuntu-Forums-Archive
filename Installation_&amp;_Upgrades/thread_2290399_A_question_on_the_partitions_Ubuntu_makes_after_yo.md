---
title: "A question on the partitions Ubuntu makes after you select &quot;erase disk&quot; w/pic"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by Badojo on 2015-08-12
I recently installed Ubuntu 15.04, during the installation process I was approached with the selection to "erase disk". Now I chose this knowing and hoping it would delete everything off my my SSD. So my question is did it? I had a opensuse distro installed before hand and I had hoped this would remove all of that with just Ubuntu software instead. However when I went to the "Disks" app on Ubuntu it shows 2 additional partitions. Are those created by the Ubuntu install in anyway? Is that normal? Picture is posted below...

[IMG]https://imagizer.imageshack.us/v2/902x507q90/905/YfE6Kc.png[/IMG]

---

### Post by mystics on 2015-08-12
I can't really read what they say, but my guess is that one is the  Extensible Firmware Interface (EFI) and the other is the swap  partition. Both of those are normal.

---

### Post by westie457 on 2015-08-12
The pic looks like a normal full disk installation.
With the MBR partition table that you are using /root is a primary partition and swap is always created in an extended partition.

---

### Post by Badojo on 2015-08-12
What does Ubuntu even to to utilize those partitions?

---

### Post by oldfred on 2015-08-12
I now prefer gpt partitioning over the 35 year old MBR(msdos) partitioning with its 4 primary partition limit and extended partition with logicals inside it.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

But if you want to dual boot with Windows you have to boot in UEFI mode which is now part of hardware in place of BIOS on newer systems.

You have to have the logical partition in the extended with MBR.
And swap is used as RAM memory overflow. Or if you load more applications that RAM can support then is uses swap. System will then be noticeably slower as hard drive or even SSD is much slower than RAM.

But if you have 4GB or more of RAM, you may never use swap. Good to have some just in case.
       
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

