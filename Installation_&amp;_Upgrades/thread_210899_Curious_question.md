---
title: "Curious question?"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by linuxnomad on 2006-07-07
I just reinstalled Ubuntu, but this time around I changed file systems I chose XFS instead of reiserfs. My question is this. Why was I not able to select or use grub, lilo was the only boot loader option given? Do you have to use lilo with XFS? Also the boot splash doesn't seem to work either, even though it is loads by default. 

I had to use the alternate disk because the graphical installer didn't work on my computer. 

I don't like lilo, but my computer loads incredibly fast.

Any ideas on how I might be able switch to grub?

---

### Post by mlind on 2006-07-07
With XFS partition you can't use GRUB :( You must make a separate /boot partition using ext2/3 filesystem.

I hope this helps.

---

### Post by linuxnomad on 2006-07-07
Thanks for the help. I wasn't sure able grub and XFS. I just desided to try XFS because I heard the boot times were faster than ext3 or reiser and they are faster. 

There isn't anything wrong with lilo its just different than what I am use to. I can live with it.

---

