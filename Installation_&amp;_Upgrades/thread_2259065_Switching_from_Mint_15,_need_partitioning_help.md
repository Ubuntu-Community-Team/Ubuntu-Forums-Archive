---
title: "Switching from Mint 15, need partitioning help"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by loonsailor on 2015-01-01
I have a dual boot system (Windows, Mint).  I want to keep the Windows partition, and replace Mint with Ubuntu, but I'm confused by what I see in the installation process.

I'm running 14.10 from a DVD, doing the install, and get to the partitioning screen.  I select "something else", because I don't want to keep Mint, but do want to keep Windows.  The next screen shows me that I have four partitions on /dev/sda.  

/dev/sda1  115GB  NTFS  Windows
/dev/sda6  260GB  ext4   Mint
/dev/sda7  256GB  ext4   Mint
/dev/sda5  7GB      swap

I have no idea why there are two separate, equally large Mint partitions.  When I boot Mint back up, I see that it's using /dev/sda7 on /, and not mounting /dev/sda6 at all.  When I mount it and have a look, it's another entire root file system.  Maybe some Mint update did this, and I never realized it until now.

Anyway, I think that what I want is to merge sda6 and sda7, and put ubuntu there, keeping sda5 as ubuntu's swap.  Is that reasonable?  If so, how do I do it?  It seems I could delete sda7, make sda6 bigger to absorb the freed up space and change it from Mint to just ext4, mounted as /, and check the format box.  Is that right?  

Thanks for any help!

---

### Post by egeezer on 2015-01-01
Easiest way: delete sda 6 and sda7, click for New partition, format it ext4, and specify mount point /.  I've done it that way many times, have never had it go bad.

Note: edit it /                                   (the /. made it look like something elaborate!)

---

### Post by loonsailor on 2015-01-01
Thanks, egeezer!

---

