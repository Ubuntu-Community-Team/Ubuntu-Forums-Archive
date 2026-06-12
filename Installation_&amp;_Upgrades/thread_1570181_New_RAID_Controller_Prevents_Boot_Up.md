---
title: "New RAID Controller Prevents Boot Up"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Orange Reaper on 2010-09-07
I have a UBUNTU Server 10.4 box configured as follows:

sda - ATA Port 0 - Boot Drive

sdb - SATA Port 0
sdc - SATA Port 1
sdd - SATA Port 2

sdb/c/d are configured as a soft raid 5 array

The box works great!

I have purchased a Startech PCI - 4 SATA card; when I add a fifth SATA drive onto this card then the box refuses to boot up - it stops part way through the sequence with a ureadahead error (without the drive but with the card plugged in everythng's fine)

Disabling ureadahead does not make any difference.

If I hot plug in the SATA Drive after booting- it's recognised and works OK (but not if I re-boot)

I can boot from the Live CD; with the drive attached; then I notice that the additonal drive has 'become' sda and all the other drives have shuffled up one (sdb becomed sdc etc).

Using udev to force the new drive to be called "pcid" does not solve the problem (I can hot swap it in and it appears as /dev/pcid - but if I re-boot then the box hangs part way through the boot sequence

I guess that the system is finding the correct drive to boot from at startup (as boot up messages are seen ok) but then gets confused and can't find the files it needs to finish the boot sequence.

Can anyone help - thanks in advance for your trouble.

---

