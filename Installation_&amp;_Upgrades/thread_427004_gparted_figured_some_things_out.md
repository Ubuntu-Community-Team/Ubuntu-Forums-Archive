---
title: "gparted: figured some things out"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by trents on 2007-04-29
I learned some things about using gnome partition manager (gparted) last night while trying to shrink one of two ntfs partitions on my drive. I thought maybe these discoveries might be of some help to others, as I have noticed several posts lately by folks trying to install unbuntu on a multiple-boot system who got stuck trying to use gparted. 

In my situation, I had two ntfs partitions (one large one for Windows XP and one small one for Vista RC1). I also had several Linux partitions for Ubuntu, both primary and logical or extended ones. The ntfs partitions were listed first by gparted, followed by the Linux ones. I purchased a retail copy of Vista this week and wanted to make the pation I would be using for it larger while shrinking the partion being used by XP. The problem was, gparted would object and throw up an error message when I tried to shrink the XP partition. I finally got it figured out and here is what I learned about the rules gparted plays by:

1. To acutally make changes to partitons, gparted must be run from a live CD, not from the Linux installed on your hard disk.

2. To make changes to a partition, it first has to be unmounted. Mounted partitons are seen by the OS as being in use already. A mounted partition will have a yellow "lock" symbol beside it. You can unmount a partition by right clicking on it and chosing the "unmount" option from the menu.

3. To delete an extended (logical) partition, you first must unmount and delet the primary partition it is associated with.

4. To increase the size of a partition you first must decrease the size of the partition that follows it in the gparted list or even delete it. I read somewhere that gparted only makes changes in a forward direction so there must be "unallocated" space after the partition you are trying to upsize.

5. When using gparted to downsize a partition, you may get an error message at the end of the process but it may be meaningless.  This happened to me when I downsized my XP partition and I thought the operation had failed. However, when I rebooted and rechecked the partions with gparted, it in fact had been downsized.

Gparted is a very capable open source utility but it's a little fussy and not as flexible, intuitive and user friendly as the commercial tools. 

Steve

---

