---
title: "Hard Drive = toast?"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Chaos_Spear on 2010-07-30
So, I started getting filesystem unstability when I installed Karmic this past March.  I had to boot into the LiveCD and run fscks every week or so.  Eventually moved to Lucid, which has been a bundle of problems up and down, so finally reverted to Jaunty, which was great for awhile but now, not only can I not boot into Ubuntu, but fsck can't find any errors in the partition.

When I try to boot, I get a DRDY error loop.

Should I just bail on this hard drive, or is solvable?

---

### Post by gordintoronto on 2010-07-30
First check for any loose cables!

Can you get to Accessories/Terminal? Then:
sudo fdisk -l
(to find out what device your hard drive is)
sudo smartctl --all /dev/sda | grep overall
(assuming sda1 is the first partition on your hard drive.)

The program is not perfect, but it should give you some indication about whether the drive needs to be replaced.

---

