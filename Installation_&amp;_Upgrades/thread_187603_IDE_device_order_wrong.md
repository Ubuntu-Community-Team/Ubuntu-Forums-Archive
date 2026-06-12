---
title: "IDE device order wrong"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by ginkgo on 2006-06-03
Hi,

  Well I can't wait to get this going, Dapper looks real promising, but here's my problem during the installation both from the livecd, and the alternate install cd everything goes fine up to the partitioning and then i notice all of my IDE devices are in the wrong order, i have 4 HD's ( 120, 40, 40, 40 ), and 2 DVD drives.

Correct Order ( As it is currently in Breezy )

 Onboard NForce2 IDE devices:
 ------------------------------------
   ( /dev/hda ) primary master:     WDC WD1200JB-00FUA0   (120GB)
   ( /dev/hdb ) primary slave:       Maxtor 2F040J0    (40GB)
   ( /dev/hdc ) secondary master:   LITE-ON DVDRW SOHW-812S
   ( /dev/hdd ) secondary slave:    LG DVD-ROM DRD-8160B
 ------------------------------------

 PCI Silicon Image PCI0680 Ultra ATA133 dual channel devices 
 ---------------------------------------------------------------------------
   ( /dev/hde ) primary master:    SAMSUNG SV4002H   (40GB)
   ( /dev/hdf )  primary slave:     ST340016A    (40GB)
   second channel unused ...
 ---------------------------------------------------------------------------

during the installation it sets up the add-in card first thus hde, and hdf become hda, and hdb, and my onboard HD's are given hde, and hdf, then my dvd drives come in as hdg, and hdh. I could proceed with the install in this order however i have used this layout for some time, and i'd like to keep it that way to avoid confusion. My main HD 120GB has 3 partitions ( Ubuntu, Data, and Swap ) all other drives are data partitions as well.  I have read through many post here with similar setups, and issues, but i have yet to find a solution.

 Any help is greatly appreciated.

---

### Post by tommcd on 2006-06-03
Did you try option #3, manually edit partition table? If you choose that you should be able to select your main drive and partition it the way you want.
Or, I suppose you could just temporarilly disconnect all other drives except the one you are installing Dapper on, then reconnect the other drives and mount them once Dapper is installed the way you want. 
Hope this helps.

---

