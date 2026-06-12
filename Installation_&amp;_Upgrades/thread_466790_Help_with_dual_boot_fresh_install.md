---
title: "Help with dual boot fresh install"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by jharadie on 2007-06-07
Hi, I'm wanting to make sure that my plans will work with Feisty Fawn.

Setup: 2 HDs, 120G & 80G.  The 120G has a bad spot that I'll have to work around.  As far as I know there's no RAID issues.

Currently running XP Home, but it's pretty messed up.  Will blow all partitions and start over.  (If it weren't for 2 work-related win-exclusive programs, I wouldn't bother with dual boot.)

Read some of the topics, seems it's best to install xp first.  Will give it only the 120G HD, with 3 partitions, working around the bad spot.  Will format to ntfs, not fat32.

Then install Ubuntu on the 80G HD, trusting that GRUB will install itself in the mbr (which is on the 120G), give Ubuntu the entire 80G HD.

This should work, yes?

After that, would somebody point me to a howto to modify /etc/fstab to mount the xp partitions?  I've seen it done before in RH, nice for moving around data.

Been playing with Ubuntu FF on a second machine, and I'm HOOKED!  My past experience with Linux has been using it as a server, though I did put Freespire on a friend's machine, to her delight.  Someone suggested I check out Ubuntu, and that was a darn good suggestion!

Thanks in advance for your comments.

:D

---

### Post by logos34 on 2007-06-07
Check out this site:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

There's also a link there somewhere to Herman's dual-boot howto.  

If these are both pata/ide drives in master/slave postitions, it's probably best to have the XP disk master and ubuntu on the slave drive because the installer will by default want to put grub on the mbr of '(hd0)', which is how it designates the first hard disk detected in the bios boot order.  This will overwrite the windows bootloader, which is fine since grub does an excellent job of booting most any OS.

---

