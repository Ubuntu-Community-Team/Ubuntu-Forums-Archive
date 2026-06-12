---
title: "ACHI / MOBO BIOS -&gt; HardDrive Aparteid"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-12-01
It's just weird to me. I'm building a new machine which boots W7 and Ubuntu 11.04. AHCI Bios is enabled. On boot, going into the mobo setup Bios shows:

IDE Channel 0/Master - none
            0/Slave  - none
            1/Master - none
            2/Slave  - none
            3/Master - none
            3/Slave  - none
            4/Master - Western Digital <-(Grub/W7/Ubuntu/Data)
            4/Slave  - Western Digigal <-(uninitialzed, for OS/X)

Before entering the mobo Setup Bios (Award), the AHCI Bios reports the following:

Controller Bus#00, Device#1F, Function#02: 06 Ports, 03 Devices

Port - 00: Hard Drive, Hitachi <-(NTFS Data drive)
       01: No Device Detected
       03: Hard Drive, Seagate <-(NTFS Data drive)
       04: CDROM
       05: No Device Dectected

You can imagine that I'm a bit perplexed as to why the (all) SATA devices are showig up (selecetively) in two different BIOS reports, AHCI and mobo BIOS. All HDs are 1-Tb. MOBO is a new Gigabyte Intel-based, with factory BIOS. Both W7 and Ubuntu boot and run fine.

Just be complete, let me add that there is a 6th HD, another Hitachi identical to the one reported by the mobo (Award) BIOS. In fact, the two Hitachi drives were part of a RAID-0 configuration in another computer. I moved them both over w/o reformatting or anything (yet). ONLY ONE (1) of the former RAID-0 Hitachi drives is recognized on the new system, though it does contain all of the expected data. The other Hitachi, when attached, simply doesn't show up ANYWHERE, either in the AHCI or Award BIOS readings, not even if I diconnect the OTHER Hitachi. I've yet to put the unrecocognized Hitachi into an external case w USB connection to test, but that's next. For the time being, I've disconected the power and data cables while I try to sort things.

Suggestions requested. Thanks.

---

### Post by RMOP on 2011-12-05
Well, for all of you monitoring this thread for activity :lolflag: the answers to the problems are:

1) a faulty power connector on a brand new Corsair PS kept one HD off-line. Moving to an upstream connector fixed that. The missing HD had nothing to do with its having been part of a RAID-1 array (I mistakenly said RAID-0 in my initial post).

2) a BIOS update now shows all drives in both the system BIOS and the AHCI BIOS

---

