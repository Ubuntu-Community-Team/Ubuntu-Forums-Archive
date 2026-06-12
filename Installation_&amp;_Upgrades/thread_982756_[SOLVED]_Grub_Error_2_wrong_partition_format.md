---
title: "[SOLVED] Grub Error 2: wrong partition format"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Stochastic on 2008-11-15
Hi, I just installed a copy of 64Studio onto a new partition and when it re-installed grub into the MBR it prevented my Ubuntu from booting.  I left the Ubuntu partition as the bootable flagged partition - I don't know if that effects anything - and 64studio boots just fine (I've even mounted all the other partitions so I can edit all files I might need).  Essentially what I could see the problem as was that the Ubuntu partition is attempting to be mounted as an ext2 filesystem by grub but it's an ext3 (if my memory serves correct).  The menu.list entry for Ubuntu is identical on both partitions so I don't think that's the source of the problem.  I tried poking around in the grub directories but didn't see any obvious partition type flag.  Is there an easy fix for this that I'm missing?

I did find the suggestion in this thread (post #19): [http://ubuntuforums.org/showthread.php?t=944088](http://ubuntuforums.org/showthread.php?t=944088) to probably be what the problem is (a too old version of GRUB).  This is just a guess at this point, but if that's the case, what version of GRUB can recognize an ext3 partition with 256 inodes?

Edit: So I went out on a limb and moved the Ubuntu grub files into the 64Studio partition; lowe + behold it worked so then I just copied the appropriate items into the menu.lst to allow for a 64Studio boot and I'm happy again!!!

---

