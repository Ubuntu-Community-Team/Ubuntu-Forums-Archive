---
title: "Install on ASUS P5E3 Premium (ICH9R RAID)?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by lhubntx on 2008-04-30
Built a new system:  ASUS P5E3 Premium motherboard with Intel X48 chipset.  Southbridge chipset, ICH9R, includes Intel RAID controller.  Configured RAID via boot-ROM for RAID1 and successfully installed XP armed with floppy containing ICH9R SATA RAID driver.  Will the "alternate-CD" for 8.04 'just work'?  Or, do I need to get/do something else?  I'd like to avoid trashing my XP install.

---

### Post by DrJohn999 on 2008-05-04
Same question here: Asus P5WDG2 WS Pro with Intel ICH7R Southbridge w/ 140 GB SATA Raid-1 pair. In the present WinXP Pro install, the controller ID's itself as an Intel 82801GR/GH SATA RAID controller. WinXP requires the Intel RAID driver diskette at installation.

So: is this really hardware raid since XP wants a software driver for it? This XP install does not use Window's "Dynamic Disk", so it's not *that* kind of s/w RAID.

Regarding trashing the WinXP install, my experience with previous Ubunto distros is good. For Hardy it looks like you can either install WUBI, which will go thru the "normal" windows bootloader to fire up GRUB and Ubuntu as a sort of VM (on the XP disk) from there; or you can install Ubuntu as a dual boot that starts with GRUB from where you can choose to start Ubuntu or XP. In this case the two have to reside in their own partitions. I've had good experience with this second configuration and am in the process of upgrading that (non-RAID) machine to Hardy.

For the machine in question here, I was unsuccessful with a WUBI install; GRUB was unable to find its menu file. So, the question is whether this was a RAID-inspired problem or something else.

I'd much rather run a 'real' dual-boot configuration right out of GRUB, thus the issue with the Intel RAID controller. But, if I do install Hardy for dual-boot and GRUB is screwed up, then I can't boot into XP either without manually restoring the XP bootloader. One alternative I guess would be to undo the RAID and use the now freed up second 140GB for a dedicated Ubuntu drive...

Thus, no Hardy install here until I can get a good answer.

BTW, the other two SATA channels on the Intel controller have two other non-RAID drives on them. Maybe this mixed configuration has stumped WUBI?

-- DrJohn

---

### Post by DrJohn999 on 2008-05-05
Never mind -- it's [fake raid]("https://help.ubuntu.com/community/FakeRaidHowto").

-- DJ

---

