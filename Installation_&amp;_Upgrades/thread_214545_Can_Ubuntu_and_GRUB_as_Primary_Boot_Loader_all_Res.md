---
title: "Can Ubuntu and GRUB as Primary Boot Loader all Reside in an Extended Partition?"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by AZJohnson on 2006-07-12
Can I install UBUNTU On this configuration without destroying all of my pre-existing Windows stuff?
I presently have two HDDs with partions that looks like this:

HardDrive one:
  primary partition 1: HP PRESARIO Recovery Stuff,
  primary partition 2: WinXP Home (WinXP multi-boot for WinXP     
                       itself, and Win2K on HDD two),
                       primary partition 3: more data

HardDrive two:
  primary partition 1: Win2K,
  primary partition 2: music, more data, backups, etc,
  primary partition 3: more data (backups, etc),
  extended partition 4: 24 gigs free<---- possible Ubuntu                          
                        install?

Objective: 
  1.) keep everything I presently have,
  2.) Use free partition 4 (24 gigs free) as extented partiton, 
      with multiple logical partitions for multiple(?) Linux 
      partitions,
  3.) Install GRUB into partition 4, and use it as primary 
      booter, having Ubuntu and WinXP as selections.
      Want GRUB to allow WinXP booter selection. 
     (GRUB doci implies this would be specified as (hd1,4).
      Seems to me that this GRUB issue is the key?

Thanks,
Alex

---

### Post by reacocard on 2006-07-12
should be fine. ubuntu doesn't mind being on an extended partition (mine is, works great). GRUB should be fine. the way i understand it, GRUB just calls XP's bootloader, which then loads windows. don't worry about it, the ubuntu installer will auto-configure grub for you.

---

