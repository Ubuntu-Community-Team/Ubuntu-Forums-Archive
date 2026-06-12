---
title: "Booting -- So Confused"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2008-06-08
I've been trying to figure out what partition my ubuntu is booting from.

I migrated my OS from the IDE hard disk (200GB) to the SATA drive (320GB)

I used the live CD

I used dd if=/device of=/device/destination

Second, I went to partition editor and flagged the destination partition as "boot"

I rebooted the pc, went into BIOS, disabled my IDE master (200gb)... so my boot priority doesn't even have my IDE listed, Just the SATA.

Grub loads, I try to run ubuntu, doesn't boot when it is at (hd0,0) I change it to (hd0,1) it boots. That means same hard disk, different partition if I'm not mistaken. 

When ubuntu loads, I type mount in terminal and it says the /dev is 198.0GB IDE MAXTOR blah blah blah.. how can this be? On top of that, my windows partiions are also moutned, which are also in the IDE.

How is it possible if I disabled the hard disk in BIOS? Can grub over-ride bios? Someone explain. Thank You

If you need some other information, Please tell me =)

---

