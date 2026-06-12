---
title: "GRUB hangs chainloading Windows XP"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by sulla on 2009-12-25
Dear all!

I have problems dual-booting with Windows XP:

My HDD configuration is:
[LIST]
[*]HDD 0 (GRUB: hd0, linux: sda): large SATA drive: GRUB MBR, 200MB /boot raid1, 120GB linux LVM raid1, 20GB empty space, rest: NTFS (all 4 partitions primary, the 200MB partition is marked active)
[*]HDD 1 (GRUB: hd1, linux: sdb): large SATA drive: GRUB MBR, 200MB /boot raid1, 120GB linux LVM raid1, 30GB ext3, rest: NTFS (all 4 partitions primary, the 200MB partition is marked active)
[*]HDD 2 (GRUB: hd2, linux: hda): ancient 20GB PATA drive with WinXP with the winXP MBR
[/LIST]

The 2 new SATA drives have a raided /boot and a raided LVM with /, /home ... partitions.

**my first GRUB problem is this:**
If I boot via my BIOS boot selection menu to the HDD2 (20G, WinXP with XP bootloader in its MBR), windows XP boots just fine. If I boot to either of the SATA drives, GRUB just fires up fine. GRUB can also start linux nicely. But GRUB fails to boot Windows XP from HDD2, it hangs at the "starting up..." message.
the menu entries I tried were
first, the standard
```
root (hd2,0)
chainloader +1
makeactive
```
then also the version
```
rootnoverify (hd2,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1
```
GRUB always refuses to boot WinXP from HDD2.
This is somehow ok, because I can comfortably chose which OS to boot to through the BIOS boot selection menu.

**My second GRUB problem is analogous**, and my BIOS boot selector is of no help there:
When installing Ubuntu on HDD0 I left a 20G partition empty, in this partition I later wanted to clone my XP installation to get rid of my ancient 20G drive (loud, hot, superfluouos). I booted to a PartedMagic CD and cloned the HDD3 WinXP partition to the 20G empty space on my HDD0. The data is there, all the files, Windows checkdisk reports no errors, it all looks fine.
Now, grub still refuses to chainload XP with the following menu.lst entry, it still hangs at the "starting up..." message:
```

root (hd0,2)
chainloader +1
makeactive

```
which, according to my understanding SHOULD work.

What am I doing wrong here?
[LIST]
[*] does the XP partition have to be marked as "active" via fdisk? currently my /boot partitions are marked "active"
[*] will WindowsXP not start up form a third partition starting at an offset of 120.2GB (in which case I could remove HDD0 from the raids, create the partitions in reversed order, readd the partitions to the raid, re-clone XP to the first partition at the beginning of the drive and hope for the best
[*] how can I get rid of my awful 20GB drive??
[/LIST]
Thanx for any ideas,
Sulla

---

