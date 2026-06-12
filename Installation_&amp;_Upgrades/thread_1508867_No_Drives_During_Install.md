---
title: "No Drives During Install"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by bc003 on 2010-06-13
I can't seem to get my hdd's to show up in the partition utility during install from cd. I've tried loading Ubuntu from the cd mounting and formating the disk in fat. I can do that, but when I try to install no drives. I tried the install disk in another computer( gateway laptop) and it worked just fine. Asus mboard w/2 sata drives. Any help would be great as I already formated my other opsys away trying to get it to pick up the drives. thnx Bill

---

### Post by darkod on 2010-06-13
This usually happens if the disks were used in raid and they have metadata remains on them. In that case the installer can "see" that and "ignores" them. Even formatting doesn't remove the raid metadata.

If you ARE running raid, you install ubuntu another way, with the alternate install cd.

If you are NOT running raid, first double check in BIOS that you have no raid options enabled by mistake, then boot into live mode with the ubuntu cd and in terminal do:

sudo dmraid -r -E /dev/sda (also for /dev/sdb if needed, etc)

If that asks you to remove settings, do it and it should be fine. If it still doesn't see the disk(s), remove the whole dmraid package all together:

sudo apt-get remove dmraid

---

### Post by srs5694 on 2010-06-13
Are you saying that the disks don't show up at all in the partitioning tool or that the disks show up as empty in the partitioning tool? If the latter, darkod's suggestion may be an explanation, or it could be a minor bit of corruption, as described [on this page of mine.](http://www.rodsbooks.com/missing-parts/index.html)

If the disks don't show up at all, then it's likely that Ubuntu is missing a driver for your motherboard's disk controller. Sometimes you can work around the problem by unplugging the cables that lead to the disks from the motherboard and plugging them into other connectors. (Some motherboards, particularly those that support more than four disks, use two disk controllers, and one may work better than the other.)

---

### Post by bc003 on 2010-06-13
Thnx Guy's Darkod nailed it got it going thnx again bill

---

