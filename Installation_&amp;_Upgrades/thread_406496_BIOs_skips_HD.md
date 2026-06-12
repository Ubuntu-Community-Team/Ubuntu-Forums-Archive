---
title: "BIOs skips HD"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by KaitenV on 2007-04-11
So check this out (my system specs):

    * EVGA 256-P2-N615-TX GeForce 7600GT 256MB GDDR3 PCI Express x16 Video Card
    * A-DATA 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model ADQVE1A16K
    * Intel Core 2 Duo E6300 Conroe 1.86GHz LGA 775 Processor Model BX80557E6300
    * MB ECS NFORCE 570 SLIT-A V5.1 775
    * POWER SUPPLY CMAX500W CR-550B BKRT
    * CASE ANTEC|P180B BLACK RT
    * Super Old LITE-ON DVD ROM
    * 20GB Samsung PATA Hard Drive (installed on)
    * 80GB Maxtor PATA Hard Drive
    * 320GB SATA Hard Drive (no plugged up)
    * Linksys network card


Now as inspected, my installation went flawlessly, but for some reason GRUB isn't picked up. I have it so it will boot to the hard drive first, but it continues on to the DVD ROM anyway. The hard drive is set to master both in the order of the IDE cables and Jumpers on the back, so, anybody know what's up?

I've been trying to get this system up since Thursday, have fallen behind on clinets and need some serious help.

Side Note: I also *tried* to install Vista RC1, but it gave me a Blue Screen of Death.

---

### Post by heimo on 2007-04-11
I'd disable booting from DVD in BIOS and then switch the order between the two connected disks (so that you try both as the first boot device). Do you get any kind of indication that it'll try to boot? ("GRUB", stage 1/1.5/2 - boot manager)?

---

