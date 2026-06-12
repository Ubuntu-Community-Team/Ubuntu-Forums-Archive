---
title: "can lubuntu and ubuntu share /boot?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by lnthai2002 on 2010-08-29
Hi,
I want to try lubuntu on my comp which already has ubuntu and win7 dualboot. I intend to make a new partition for lubuntu 's '/' and let it share /boot with ubuntu. Would that cause any problem?

---

### Post by arrange on 2010-08-29
How do you want it to be shared? Extra partition for */boot* or something else?

---

### Post by oldfred on 2010-08-29
I do not recommend separate /boot and sharing is a very bad idea. The files are not large especially if you occasional houseclean. 

The second install will overwrite the first install's grub files and may not have the same kernel versions.

I also do not recommend sharing /home as settings may be different but you can easily create a /data partition and share that. I have several Ubuntu installs each in 20-25GB partitions but all my data is in data partitions one NTFS for my old XP which I now use only for one app and most of my data is in a ext3 partition.

---

### Post by lnthai2002 on 2010-08-29
Here is my current spec:
hda1 : windows 7
hda2 : system files for windows 7 (or something like that, it was there when i install windows 7)
hda3 : mount to /boot for ubuntu 9.10
hda4 : 1st partition : SWAP for ubuntu 9.10
       2nd partition : lvm partition mount to /home for ubuntu 9.10

This is what i am thinking: make a new logical partition in hda4 and install lubuntu there, basically this partition is mount to / of lubuntu. I was thinking about mount hda3 to /boot of lubuntu too.
Even if i make a completely new partition for lubuntu how does GRUB knows that I have 3 OS ?

---

### Post by oldfred on 2010-08-29
If you install lubuntu's boot to the current boot you will destroy your boot of Ubuntu.

Grub's osprober searches system and finds all the boot files and adds each to the grub menu.

---

### Post by lnthai2002 on 2010-08-29
When I install ubuntu, at the last step it ask where I want to install grub, I suppose lubuntu gonna ask the same question, what should I answer for that? I already have grub installed on mbr when i installed ubuntu 9.10.

---

### Post by oldfred on 2010-08-29
It just depends on which system you want in control Ubuntu or Lubuntu. Either one should find the other and let you boot both.

---

