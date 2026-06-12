---
title: "How to install Ubuntu 8.04 LTS AMD64 desktop on a separate partion &amp; dual-boot XP Pro"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Jabbadahut on 2008-05-25
Hi, I am needing assistance.  I would like to dual boot XP Pro & Ubuntu 8.04, but I would like to install the latter on a separate partition.  I tried using the "Guided install" option where Ubuntu creates a new partition on the same hard disk where Windows is installed, but I had a problem with getting GRUB to start, (see [http://ubuntuforums.org/showthread.php?t=805578]("http://ubuntuforums.org/showthread.php?t=805578") for more information) and I wish not to go through that rigmarole again.

So, what I tried to do was use Partition Magic 8 to create a new partition from the free space where XP is at, one for ext3, & one for swap.  Then I tried installing Ubuntu from the CD (didn't use Wubi), & chose manual, because I didn't want to mess things up like I did last time.  However, when I chose the ext 3 partition, the install gives me an error stating I don't have a root installed.  I then canceled the install, rebooted back to XP, and deleted the partitions I created as I am not sure how to proceed.

How can I install Ubuntu 'manually'?

---

### Post by Franc88 on 2008-05-25
Hi, I too had issues installing 8.04 as a dual boot into my laptop running XP Home.  I finally got it to install after some suggestions from the good folks here.  It did take me a total of a 36 hours to get the whole thing working so it wasn't easy but well work the effort.

Try searching for a HowTo on doing the installation and it will probably have something in there about how to do the partitions manually.

I ended up having to not use the LiveCD version and used the alternate version and partitioned the HD like good ole FDISK.:)

---

### Post by jean noel on 2008-05-25
> **Jabbadahut said:**
> Hi, I am needing assistance.  I would like to dual boot XP Pro & Ubuntu 8.04, but I would like to install the latter on a separate partition.  I tried using the "Guided install" option where Ubuntu creates a new partition on the same hard disk where Windows is installed, but I had a problem with getting GRUB to start, (see [http://ubuntuforums.org/showthread.php?t=805578]("http://ubuntuforums.org/showthread.php?t=805578") for more information) and I wish not to go through that rigmarole again.

So, what I tried to do was use Partition Magic 8 to create a new partition from the free space where XP is at, one for ext3, & one for swap.  Then I tried installing Ubuntu from the CD (didn't use Wubi), & chose manual, because I didn't want to mess things up like I did last time.  However, when I chose the ext 3 partition, the install gives me an error stating I don't have a root installed.  I then canceled the install, rebooted back to XP, and deleted the partitions I created as I am not sure how to proceed.

How can I install Ubuntu 'manually'?
For manual installation of Ubuntu: Essential reading on [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty).
just follow the instructions. Absolutely lovely site for Ubuntu; next after the forums
:)

---

### Post by Jabbadahut on 2008-05-25
> **jean noel said:**
> For manual installation of Ubuntu: Essential reading on [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty).
just follow the instructions. Absolutely lovely site for Ubuntu; next after the forums
:)

Hurrah!  It works! Thank you, thank you, thank you, thank you, thank you! :D

---

### Post by meierfra. on 2008-05-25
> Thank you, thank you, thank you, thank you, thank you

The best  to thank somebody is to click on the blue ribbon  with the goldstar which you'll find next to each post.

---

### Post by Pumalite on 2008-05-25
+1

---

