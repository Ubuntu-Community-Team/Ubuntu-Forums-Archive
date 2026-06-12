---
title: "Existing Hard Drive"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by rsouthard on 2010-07-20
I have a 160GB HD that is currently being used as storage. It is formatted NTFS but has no OS installed. I would like to Install Ubuntu onto this HD while retaining the existing Data. What will be the easiest way to partition the HD and Install Ubuntu? Any help/advise is appreciated.

---

### Post by oldfred on 2010-07-20
Since it is not a system partition you can shrink the NTFS partition and install. The installer will automatically shrink it in a side by side install but if you want control over the sizes of the partition(s) you can manually create them in advance or as installing.

The minimum I recommend is 20-25GB for /root and 2GB for swap. If you want to hibernate you then should make swap slightly larger than your RAM memory. Old instructions when RAM was only 256MB was swap should be twice RAM but with 2GB or RAM or more you will rarely use swap.

If you want a separate /home then the install can be 10-20GB and make /home larger as that is where your data and (hidden) user settings is stored.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Yours is similar to a dual boot without the windows system install issues on the same drive. See herman's link above for two drive issues. Most importantly is the advanced button on the last install screen on where to install grub as you will want it installed to the MBR of the 160GB drive and set BIOS to boot that drive.
Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

### Post by theozzlives on 2010-07-20
It depends on if you want to keep using the NTFS partition. If you do then resizing is the answer. If not, select use whole drive when installing. Welcome to Ubuntu.

---

