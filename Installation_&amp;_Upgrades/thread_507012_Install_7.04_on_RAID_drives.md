---
title: "Install 7.04 on RAID drives"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2007-07-22
OK here is my hard drive set up...

Two 250Gb SATA II Drives, using the RAID controller on the MoBo. So I have it configured as one fat, but fast drive around 500Gb (Stripping)

One IDE 160Gb drive that I use as a backup 
One IDE DVD writer (Separate IDE channel to the 160Gb unit)

The rest of the spec...
MoBo is an ASUS K8N4-E
2Gb RAM
Sempron 63Bit 3400
BFG nVidia 7900 256Mb GT OC
Soundblaster Audigy SL

WinXP is installed to the RAID using a 100Gb partition, the rest is empty. The 160Gb IDE is also empty.

I would like to install Feisty on the empty portion of the RAID drive and have the 160IDE one as a back up again.

On installing ubuntu it can see the IDE drive OK but it sees the SATA II drives as two individual drives not as a single RAID Drive. I can install ubuntu on the IDE drive just fine (that's why it's empty...) Grub is on the IDE drive so isn't seen at boot up. The only way to get in to ubuntu is to F8 at POST and get the MoBo BIOS to allow me to choose the boot device. Then if I point at the IDE drive then Grub takes hold and boots ubuntu normally. I can live with the whole F8 thing at boot up, it will keep the wife happy when see uses the computer. 

However it still doesnt help me with getting ubuntu to install on to the RAID drive. 

Before I attempted to install ubuntu on this box I want to see if I could shrink the RAID drive using GParted. I used the latest CD image for the disk. When GParted couldn't see the RAID I should have know that I was going to run in to some issues...

Is there a nice tidy answer to this? a driver on install I could use? If not I will simply have to put ubuntu on the slow IDE drive and continue the F8 routine at boot up.

---

### Post by Pumalite on 2007-07-22
Raid arrays are not a good idea in Linux, but if you insist; here is something to read:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

