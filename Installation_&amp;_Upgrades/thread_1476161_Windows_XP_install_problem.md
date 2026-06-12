---
title: "Windows XP install problem"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by evo9 on 2010-05-07
So far with 10.4 I've been able to dual boot with vista np, but when I try with XP it says there is no HDD found, then kicks me out of the install. This has happened with two XP disks. I'm wondering if this is an issue with the dual boot with linux, as I have used both of these cds to install xp before.

Any ideas?

Thanks

also note, I have taken vista off the hdd currently I'm only running ubuntu

---

### Post by oldfred on 2010-05-07
XP will not see any ext partitions. You need to have a primary partition with NTFS format.

---

### Post by Objekt on 2010-05-07
By "taking Vista off the hdd," do you mean you deleted the partition Vista was on, or did something else?

If you reformatted Vista's system partition as an ext3 or ext4 volume, the XP installer will not see it, as the reply above suggests.  You will need to go into Ubuntu and either reformat the former Vista volume as NTFS, or delete the partition entirely.  

If you do either of those things, the Windows XP installer should see the freed space and allow you to proceed.

---

