---
title: "Totally stuffed up attempt at dual boot installation"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by beninpoland on 2007-12-05
Hi

I tried to install Ubuntu on my computer where I am already running Windows XP. I wanted to do dual-boot as I am not quite ready to jump with both feet in to the new and exciting linux world.

I currently have two partitions (C: for windows, D: for data) and I was going to shrink D and create new partitions for ubuntu, for swap and for a FAT-32 to share between the two.

I totally stuffed up the install (I am sure I messed up regarding Grub and the MBR being a newbie).

The result is that I was getting "operating system not found" after the BIOS had finished.
I used the Windows recovery console to fixboot C: and tried fixmbr but neither worked. I believe the problem is that C: is not set as the active partition because if I use the Windows XP install CD I get a message about this.

How can I fix the active partition? I don't have a windows recovery CD to boot to the desktop. Can I do it from Ubuntu using the live CD? I had a look at Gparted but didn't see any options for setting partions as active or not.

Thanks in advance.

Ben

---

### Post by beninpoland on 2007-12-05
Hi

Actually I fixed this myself - I started the new install dialogue from the Windows XP CD, choose partition C: to install it on, accepted the warning that the installation would make it active and this might upset my "other operating systems", and then quit the install.

I can now run windows again.

I will now go and read up on how to do a dual boot installation properly, and spend a bit more time studying Grub!

Thanks.

Ben

---

### Post by Pumalite on 2007-12-05
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

