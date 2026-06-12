---
title: "server locked down"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by kezeb on 2012-02-17
i've a dell poweredge sc1435 i'm trying to install ubuntu server on it but it won't let me partition the drives. i just don't have any ideas on what to do

---

### Post by darkod on 2012-02-17
Can you give more details what happens when you reach the partitioning step? Maybe even a photo of the screen + explanation what you want to do?

---

### Post by Dangertux on 2012-02-17
Did you initialize the RAID array first?

---

### Post by MAFoElffen on 2012-02-17
> **Dangertux said:**
> Did you initialize the RAID array first?
Additional to that- That server came with SAS or SATA drives. Which is yours? If SATA, SATA 3? Any external drives?

Your 1U rackmount case only has internal 2 drive bays. The RAID controller for it was an option (SAS 5/iR)

I have a similar server board... that is a little older. You have 2 Broadcom Gigabit2 NICs., where mine are Broadcom NetXtremes... For mine and Ubuntu server installs, I have to load non-free firmware for them during the install. Wondering if the same may be for yours... But that is a step later than the partitioner. May or may not be.

---

### Post by MAFoElffen on 2012-02-19
Just a few tidbits that might help- adding to my last post and where the questions where leading.

If SATA 3, get into your BIOS Settings and make sure the BIOS sees your drives. Then change the BIOS Hard Disk Mode from IDE to AHCI. Some boards you can set the whole controller to ACHI and it works. Some boards you have to set every drive individually to AHCI.

If you have any accessory cards (external drive or RAID), go into each card's BIOS settings and ensure they can see their attached drives. If the attached drive(s) you can't see are SATA 3, follow the instructions above.

If SAS... then as far as I know at this moment, I consider them the same as SATA 3.  I can interchange both drives on a SAS backplain.

If RAID, even if set to JBOD, make sure the drives are marked online.

I have a particular server board that everytime I boot it, it shows the local attached drives in the BIOS messages- boots and runs fine--> except if I start the partitioner those drives are not seen.   That same, if I get into BIOS settings, go to and probe each drive, exit (saving or not)--> then they are seen in the partitioner. 

Hope these tidbits help.

---

