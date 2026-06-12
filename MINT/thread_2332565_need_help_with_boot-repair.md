---
title: "need help with boot-repair"
date: 2016-08-01
forum: MINT
---

### Post by Stanley Krute on 2016-08-01
I've got a system that dual-boots LinuxMint 17.3 and Win7. 

I moved the Linux partition with gParted, then ran boot-repair to make sure booting would work. 

BootRepair did not offer a boot repair option, just the creation of a BootInfo summary. 

Here is that:   [http://paste2.org/pGxw7CC4](http://paste2.org/pGxw7CC4)

Anyone have any ideas on what i need to do to be able to boot again ? 


thx

---

### Post by jeremy31 on 2016-08-01
*Thread moved to **MINT**.*

---

### Post by oldfred on 2016-08-01
It seems to have dumped an error on blkid. Which I have not seen before.

Are sdf, sdg & sdh external drives?
I might unplug those and see if it boots or Boot-Repair works.

Boot-Repair says UEFI Secure boot may be on, but everything you have is BIOS based. Make sure if UEFI hardware Secure boot is off.

You show a partition error on the protective MBR for sdh. The MBR entry for the entire drive to prevent old partition tools that only recogize MBR, should be just one gpt entry for entire drive.

       repair gpt:
Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 

[URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

### Post by Stanley Krute on 2016-08-02
> **oldfred said:**
> It seems to have dumped an error on blkid. Which I have not seen before.

haha, I love seeing at least one new cybernian surprise daily !!

> **oldfred said:**
> Are sdf, sdg & sdh external drives?
I might unplug those and see if it boots or Boot-Repair works. 

Yes. Unplugged. boot-repair came up properly, with its fix option, and it worked !!  

[ I copy/paste-lost the URL of the boot-repair report, dang !! ]

Thank you ever so much for sharing of insight. 

Will be doing the MBR/gpt repairs .... 

-- stan

---

