---
title: "Ubuntu Installer Doesn't Detect HD"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by vdorta on 2005-07-12
I tried the Ubuntu LiveCD and liked it very much although it didn't detect my PCI wireless card. I went ahead anyway with a fresh installation CD but this time the Ubuntu installer gives me a "no partitionable media detected." I had previously partitioned my SATA hard drive with BootIt NG, I have Windows XP on 60GB and left 20GB of free space for Linux, plus a 500MB FAT32 partition for shared files.

It appears that Ubuntu can't see my hard drive. Any ideas?

MSI Rs480 mobo, AMD64, Samsung 80GB SATA

Thanks,

Val

---

### Post by kosmic on 2005-07-12
Hello, I've had the same problem with one of the machines in the office, you have to go to your bios and change an option in the disc, something to do with Raid Type, i can't remeber now the exact name :(


hope it helps

---

### Post by vdorta on 2005-07-13
Thanks, I understand what you mean and I also believe it has something to do with my SATA drive. My MSI RS480 motherboard's IDE controller handles SATA drives too and I know I have the correct setting; I don't use RAID and my Windows XP installation works well.

EDIT: I am posting this addendum to help all those who will search for an installation glitch similar to mine. I haven't found a fix for this problem, which is not exclusive to Ubuntu, after trying almost a dozen distros and finding only one (Ark Linux) that was successful in installing. The source of the problem seems to be the motherboard chipset (ATI Xpress 200), which is not Linux friendly at all.

---

### Post by robbish on 2005-07-25
Hey, i have the exact same problem.. :) Has anyone find a solution yet?

---

### Post by porter on 2005-07-25
i have the same problem, i still haven't seen post in this forum with any solution yet.

---

### Post by Jiilik on 2005-07-27
I also have the same problem, however it seems the issue is with kernel 2.6.10 -- it is solved in 2.6.11 - so if you can somehow get the thing installed and upgrade to 2.6.11 you are set.

I'm still trying to figure out if there's a way to tweak the install cd to use 2.6.11

---

