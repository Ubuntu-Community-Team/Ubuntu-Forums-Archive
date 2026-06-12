---
title: "Ubuntu can't find SCSI raid HD"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by Natura on 2005-06-02
Uuum. I m newbie for linux nd I just bought Old IBM e-server 200.
This  server has 2X18Gb internal SCSI Hard drives. I think bios setting is correct but, ubuntu install CD can't find any HD to install  ](*,) ?! Seems missing Disk controller driver ?
I tried with Debien install cd nd can't find HD at all too. Debian install CD has Floppy's driver install option before partitioning but not in Ubuntu CD.
Possiblly, my SCSI Hard drives are dead however IBM bios can recognize raid option with 2 disks on re-starting... how can I install SCSI driver for Ubuntu ?

ThX in advance. :wink:

---

### Post by alastair on 2005-06-02
I have not researched what SCSI h/w is in this box, or the config.

However, if the SCSI disks are set to be some sort of RAID (e.g. via the BIOS), this might not work. If you can see an option in the BIOS to turn OFF any RAID configuration (so they are single disks) then do it, and try again.

---

### Post by Natura on 2005-06-03
Hiiiiii, Cheers Mate.
Yes Raid option is On.
I didn't know impossible to install ubuntu OS on Raid disk.:-? 
however why it's impossible :-x ? I want to use this raid option to my server speed up... \\:D/

---

### Post by Natura on 2005-06-03
Uuum. I didn't tchek yet but SCSI card is adaptec, dunno which model.
I found also, I ll have boot problem of grub on scsi raid disks.

Ooops, BTW, Ubuntu has SCSI raid driver install option via floopy like Debien does in a middle of System install ?

---

### Post by Natura on 2005-06-07
I spent quite long to find Surport CD nd BIOS update disk on IBM site. they have massive quantities documents nd so hard to identify good firmware & driver update.
ThX for yr help, Now I installed Ubuntu 5.04 on SCSI Raid HD.

---

