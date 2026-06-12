---
title: "After reinstall Linux Mint grub menu gone with Ubuntu on LVM"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by pcdyck on 2014-11-03
Hi, my problem is a bit unique in that I encrypted a whole partition /dev/sda6 with LUKS.  I repartitioned the encrypted partition to three new partitions: / swap and /home. Here I installed Ubuntu, I believe 13.04.  For the same installation I used /dev/sda1 as /boot.  I am quite sure it was after this that I installed Linux Mint 15.  I just found out that I needed to upgrade the latter distro which I proceeded to do upgrading it to Linux Mint 17 from the LiveCD.  When it came to the partitioning section I chose the "Something else" I believe it is.  I used /dev/sda2 for /, /dev/sda5 as swap, and /dev/sda7 as /home, just like I had it on the Linux Mint 15 setup.  I left the default for Grub on the sda.  However, now when I boot the computer it does not give me a Grub boot menu, therefore I am not able to boot Ubuntu on the encrypted partition anymore.  I am very concerned about that as I have a lot of data there that I need.  If anyone would be so kind as to help me fix this menu issue I would be very grateful.  I am not much of a geek so some detailed instructions is what I need, please.  Thank you very much in advance for your help.  Pete

I reinstalled Linux Mint 17 and this time had it install GRUB in the same partition as /, ie. in sda/2.

---

