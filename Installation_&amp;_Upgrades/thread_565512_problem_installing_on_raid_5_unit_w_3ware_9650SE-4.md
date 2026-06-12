---
title: "problem installing on raid 5 unit /w 3ware 9650SE-4LPML"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by darthraider on 2007-10-02
I've been struggling the last 2 days to get a new ubuntu (7.04) setup running on a new system with a 3ware 9650SE card; using a raid 5 setup with 3x 500gb (wd5000ys, firmware: 09.02E09). All disks passed the tests provided by WD. On creation of the raid5 array, I set the first partition to be 30G in size.

What happens during install (with desktop & server edition): 
- system boots up
- raid controller shows 1 unit consisting of a working raid 5 array.
- ubuntu menu shows up
- i continue with the regular setup, all i fine, up until to the point where the setup is going to make 
the partitions. 

From here, depending on the boot parameters (noapic, nolapic, acpi=off) i get to see either 1 disk (of 30G, where's the other?), or 2 (30G + 960G). 
Whatever i pick, when i reached the screen where i have to confirm to save the partition setup and i press enter, the system hangs. 

Output on console screen (alt-f4) :
Reading all physical volumes.
Cache synchronization completed:unit=0

*system locks up* screen turns black, no response to keyboard. Have to manually reset the machine.

I have also tried various raid controller settings (StorSave, Queuing, Write Cache), but no succes.

I have tried to prepare the disks by pre-building the partitions using a Knoppix cd. This seems to work OK (no errors from fdisk). But ubuntu seems to have a problem with it.

An other weird problem, which happened 2 times now (been unable to reproduce it 'manually'), is that the controller starts to rebuild one specific disk of the array. Removing that disk from the controller/array, and for example using a single disk as target for the installation (while connected on the raid card) , doesn't work either.

I was hoping to be abled to install ubuntu 'out-of-the-box' on a raid5 array, because of the native driver support for this card.

Am i terribly mistaken or did i miss something?

---

### Post by darthraider on 2007-10-03
**solved**

It seems that the SB600 chipset on the motherboard is not fully 64bit compatible, contrary to what is told in the documentation. After booting with only 2G RAM instead of 4G, ubuntu succesfully detected all disks/arrays and making partitions did not cause any lockups.

Reference: [http://www.mail-archive.com/linux-ide@vger.kernel.org/msg06174.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg06174.html)

---

