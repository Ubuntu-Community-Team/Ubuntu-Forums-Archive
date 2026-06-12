---
title: "Restore WinXP on GRUB"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by PhoenixP3K on 2006-06-02
I installed Dapper today and I got myself in quite some trouble. I like to dual boot for many reasons but this time around when I installed from the live CD instead of telling Dapper to use as much free space it could get I selected that it had to use the entire disk.

Now my problem is a bit more complex. I have a 30GB IDE primary and a 250 GB SATA secondary. Windows XP Pro is installed on the second hard drive. And it's MBR was on the first disk. So what I should of done is let Ubuntu use the free space + this way it would of detected Windows XP on the MBR of the 30 GB HDD. Now a few weeks back I had problems with using fixmbr and ended up screwing my entire NTFS partition.

The reason why I feel this is problematic is how Windows XP CD is supposed to add itself to the MBR on the 30 GB that doesn't have a standard windows partition. Moreover Windows XP Pro at first could handle hard drives larger than 131 GB. Meaning the CD doesn't recognize my 250GB hard drive making a restore install unlikely.

So my Ubuntu is in perfect shape, I was just hoping there was someway to salvage all this. sparing me both a Windows and Ubuntu reinstall.

---

