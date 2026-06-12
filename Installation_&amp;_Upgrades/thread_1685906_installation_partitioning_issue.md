---
title: "installation partitioning issue"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by tbthyssen on 2011-02-11
Hello guys.

Im trying to install ubuntu 10.04.1 LTS on my laptop from a cd, but when I come to prepare partitions in the installation I can't see any partitions.

I have two hds and want to install ubuntu alongside with windows xp on there own hd, already got windows xp installed,

what can be wrong?

Kind reagrds

Thomas

---

### Post by Quackers on 2011-02-11
Welcome to UF :-)
Is there any unallocated space on the drive you want to install Ubuntu on? (Not free space, within a partition).

---

### Post by topher-t-mill on 2011-02-11
If windows is on one drive and the other is an empty drive then you can either use the installer and specify which partition to use manually or set it up using Gparted allowing part of the drive to be used as swap say 512mb or more. If you use the installer you can double check that the windows partition is not going to be used.
You will need to set the linux  drive mount point as / then Grub will pick up windows when it installs.
I have  done these manouvers but not with new equipment, just old desktops and laptops, so please don't send me a bill if you wipe it all . Back up important files and if you don't want to lose windows disconnect the drive when installing and then use recovery mode to update Grub.
You could use Gparted just to take a look at the drives without applying any changes and listen to Quackers as he will know a lot more than me!

---

### Post by tbthyssen on 2011-02-12
Problem solved.

Thanks guys

---

