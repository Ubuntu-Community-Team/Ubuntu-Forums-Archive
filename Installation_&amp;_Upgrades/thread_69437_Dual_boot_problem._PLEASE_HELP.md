---
title: "Dual boot problem. PLEASE HELP"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by Villenya on 2005-09-26
Hello, i am trying to get dual boot w/ ubuntu and xp. The problem is that i installed ubuntu before xp. After i install xp, i can't boot from ubuntu any more. It automaticly boots xp. i tried to boot with the ubuntu install disk and tried to reinstall GRUB, but errors were displayed and installation failed. I really need to get back onto ubuntu, what do i DO?

---

### Post by Emerzen on 2005-09-26
Are you sure XP didn't overwrite your Ubuntu partitions?  I would go to [www.distrowatch.com](www.distrowatch.com) and download a copy of Knoppix (you may be able to do this w/ Ubuntu live CD but I'm not sure).  Knoppix is a liveCD w/ lots of tools.  Anyway, download Knoppix and burn the iso.  Then boot from Knoppix and look at your harddrive (qtparted is on there and it's fine for viewing partitions).  If you still have an ext3 partition, then you still have your Ubuntu.  If that's the case, then search these forums searching for "reinstall GRUB."  I've never done that before, so I'm not sure how, but I've seen lots of posts about it.  If XP wrote over Ubuntu, then just reinstall Ubuntu on a separate partition than XP.

---

### Post by mlomker on 2005-09-26
If you posted more details about the error then we might have a better idea.  To reinstall grub it is **grub-install /dev/hda** or whatever your device name is.

---

### Post by longtex on 2005-09-26
[QUOTE=Villenya]Hello, i am trying to get dual boot w/ ubuntu and xp. The problem is that i installed ubuntu before xp. After i install xp, i can't boot from ubuntu any more. It automaticly boots xp. i tried to boot with the ubuntu install disk and tried to reinstall GRUB, but errors were displayed and installation failed. I really need to get back onto ubuntu, what do i DO?[/QUOTE]

What I have found over the course of about a dozen dual-boot installs with XP and almost any Linux is that the Linux partition editors don't cope very well with XP's NT File System. 

After the first couple of disasters I have taken this actions: (1) Either install XP first or leave it alone if it's already on; (2) Use PartitionMagic (I think I gave like $20 for it as a download) and partition the drive FROM WITHIN XP; (3) Install the Linux on the new partition.

HTH - It's worked just fine for me.

---

### Post by mctavish on 2005-09-27
Reinstalling grub from a boot disk is not that simple.

IIRC you will have to mount the root partition on your original install somehow and then chroot (change root) to it before running the grub-install command.

As someone said above, do a search on "reinstall grub" and you should be able to find more info.

---

### Post by mlomker on 2005-09-27
> Reinstalling grub from a boot disk is not that simple.


Have to admit that I've never tried the **grub-install** command but somebody told me that it works fine.  I've always used the instructions similar [to these,]("http://www.sorgonet.com/linux/grubrestore/") but that's likely to scare someone new to linux.  :)

---

