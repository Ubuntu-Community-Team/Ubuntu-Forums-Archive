---
title: "Can't mount data drives"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by FrankVdb on 2011-01-09
Hi everyone,
I installed 10.10 on my workstation but now my system refuses to mount two existing two data drives that were already there...
sudo mount /dev/sdc /mnt/data-b
gives me:
mount: unknown filesystem type 'isw_raid_member'

I didn't change any BIOS settings... My BIOS is not configured for RAID at all, that setting reads AHCI, which should be okay for my kernel (using the stock 2.6.35-24).

I tried to force mount one of the drives with
sudo mount -t ext3 /dev/sdc /mnt/data-b
but this gives me an even stranger message:
"/dev/sdc already mounted or /mnt/data-b busy
(neither of them are true...)

It's mainly the "isw_raid_member" thing that troubles me... I didn't and don't have a RAID system at all..

Thanks for any help...

---

### Post by FrankVdb on 2011-01-09
I found it. I forgot my motherboard is in fact a RAID motherboard. In spite of the fact that the BIOS was not configured for RAID, Maverick probably recognised it as a RAID motherboard, so I removed dmraid with
sudo apt-get remove dmraid

After a reboot, my data hard drives showed up nice and clean.

---

