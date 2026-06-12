---
title: "Ubuntu and Gparted fail to partition hard disk"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by ubiubi on 2008-11-08
Hi
I recently replaced my AM2 motherboard with an Intel board. The hard disk (under the original Motherboard and seven partitions prepared and created under Gparted. Five partitions were used with XP and Uuntu. The other Partitions were empty. After installing the new motherboard xp worked ok from the old grub menu but ubuntu refused to boot. Itried to reinstall ubunt but the installation failed at the disk partition section of the install. I just got a greyed screen with the buttons for next screen but no partitions displayed. A psclos and Fedora installation similarly failed. Finally the Gparted live disk also refused to show any partitions. (These are all visble in disk manager under XP.Any ideas anyone?
Many thanks

---

### Post by Mr_JMM on 2008-11-08
You say you have 7 partitions, how many are primary?

This needs to be limited to 4. Extra partitions are created by creating a max of 3 primary with the 4th as an extended. This extended partition can then be home to several logical partitions. It could be that your previous MB allowed more than 4 Primary and new doesn't. Just a guess.

---

### Post by ubiubi on 2008-11-08
Thanks for your reply
I have three primary partitions and the rest on a fourth(extended) partition.
1: XP
2: FAT 32 (Empty)
3: Ubuntu root
4: Extended a) NTFL (XP data)
            b) Ubuntu data
            c) ex3 (Empty)
            d) Swap

Cheers

---

