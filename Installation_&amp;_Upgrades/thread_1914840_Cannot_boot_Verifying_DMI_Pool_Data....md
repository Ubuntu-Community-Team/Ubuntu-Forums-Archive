---
title: "Cannot boot: Verifying DMI Pool Data..."
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by ubionenine on 2012-01-25
Hi,

I inherited a monster of a computer from a friend without the harddrives. It's home made and was running windows fine before with his hard drives.

When trying to boot my 11.10 64 bit Ubuntu installation, I keep getting stuck on "Verifying DMI Pool data..."

I believe it has for specs:

A Gigabyte motherboard (maybe S series)
A 3TB Barracuda XT harddrive.

So this is what I did:

I tried booting from a windows xp cd. The drive formatting was taking too long so I stopped it (probably a bad idea). I then booted from an ubuntu x64 LiveCD. Ubuntu can run fine off the cd and when I installed it, it all seemed to go fine. Then after installing (just one partition of 3TB) I got the grubrescue prompt when trying to boot. I read on the forums about the problems with over 2TB so I reinstalled it with a few different partitions:

1TB mounted on (/) ext4
1.50TB mounted on (/home) ext4
20 GB swap
(in that order)


500GB mounted on (/boot) ext4
1.50TB mounted on (/) ext4
20 GB swap

When looking in the BIOS it seems that there is only at "Hard Disk" option to boot. The individual partitions are not showing up? When I run ubuntu from the CD the partitions show up fine in the table though


All of the configurations are now giving me the "Verifying DMI Pool Data..."

I even tried switching the cables that connect to the hard drive, but that doesn't seem to be doing anything either.

Any help would be greatly appreciated!

---

