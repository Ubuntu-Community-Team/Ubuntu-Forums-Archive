---
title: "Moving GRUB from MBR to Linux Partition AFTER Install"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by LukeLinux on 2010-12-11
Hey guys!

Hopefully this will be an easy one. Basically what's going on is, I'm going to have to reformat my Windows partition and reinstall it to fix some massive issues I've been having with Windows lately (I'd love to be Linux-only, but unfortunately I'm required to have Windows for a couple programs that WINE just doesn't yet support). This would be all well and good, except that doing that would also have the side effect of wiping out GRUB, and that means I'd have to do a total Ubuntu reinstall (yes, I've tried reinstalling GRUB from the Live CD; it just won't work for some reason).

So what I want to do is just move GRUB from the MBR to my Linux partition so I can then add an entry for it in the Windows bootloader using EasyBCD, and thereby preserve my Ubuntu installation from having to get wrecked as well.

Can anyone help me move GRUB like that? (using 10.10)

---

### Post by efflandt on 2010-12-11
It might help if you show the output of **sudo fdisk -l** (small L) so we know what type of partitions you have.

I know that grub2 can be put on a "**primary**" Linux partition, because I had to do for my desktop when a Win7 program (probably Dell DataSafe) was storing data in what it "thought" was an unused part of the mbr, which trashed grub2 in the mbr.

Since Dell already had 3 partitions, my Ubuntu is on primary partition sda4 (with no swap, since I have 8 GB RAM).  So I installed grub2 on sda4, restored the standard Windows mbr, then used gparted to mark sda4 as the boot partition.  The Win mbr boots grub2 on sda4 without having to use any other boot loader.

But I do not know if grub would work installed to an "extended" or "logical" partition because I have never tried it (lilo used to work on an extended partition).

Scroll way down on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) to **"**Reinstalling GRUB 2" about how to **grub-install** from live CD or iso on USB.  However, you will need to use grub-install **--force** option (and ignore the warnings) to install grub to a partition.

---

### Post by Quackers on 2010-12-11
It would be less troublesome to re-install Windows to its partition and then re-install grub2 to the mbr from the live cd imho.

---

### Post by Rubi1200 on 2010-12-11
As above: please let us see more of your setup with the fdisk command.

Also, although I would not normally recommend it, you might want to consider using a separate /boot partition and install GRUB to it.

But, if you could provide more details on why exactly reinstalling GRUB did not work, it would really help us.

Thanks.

---

