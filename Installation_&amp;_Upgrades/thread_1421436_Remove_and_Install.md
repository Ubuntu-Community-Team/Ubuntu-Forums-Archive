---
title: "Remove and Install"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by stevie1989 on 2010-03-04
Hey, lm running Linux Mint 7 and XP Home SP3

25GB is Linux Mint 7 (M7)
125GB is WinXP Home SP3

WinXP came pre-installed, so l don't have a disc for it (Of course)
Linux Mint is too slow as l just don't like it (Been using it for about 3 weeks)
So now lm wondering, how do l take out M7 without screwing my XP up and install ubuntu? l know, just delete the partition, but lm worried about the Grub, l want Grub gone before l delete the partition? Also whats the best file system too install as l want too easily go into the WinXP drive (like SongBird and VLC) without having too log as a Sudo Admin access? Sorry l just want some confirmation before l go through this.

Also, running AMD Athlon 3200 2.20 GHz 1GB DDR333 Ram (lm expanding too 2GB soon).
Danke!

---

### Post by darkod on 2010-03-04
You really don't need to restore windows bootloader if you are installing ubuntu right away. However, if you still want to do it the easiest way is using ubuntu cd. Boot into the live desktop (Try Ubuntu), and if you have only one hdd in terminal run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will install generic mbr on your hdd. If you restart without the ubuntu cd, it should load XP directly. But your Mint partition is still there.

After XP is loading correctly, you can delete the mint partition either from windows Disk Management, or again from ubuntu live desktop in Gparted (System-Administration). Leave that space as unallocated.

Then when you decide to install ubuntu, just tell the installer in step 4 to Use Largest Available Free space. That will install it into the unallocated space left by deleting the mint partition.

But if you want some specific partition setup, you have to use manual partitioning in step 4.

---

