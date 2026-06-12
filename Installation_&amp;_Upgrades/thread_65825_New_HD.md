---
title: "New HD"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by pinbrook on 2005-09-15
I've just popped a new HD into my Dell Notebook, and now tried to install ubuntu from CD (install disk)

I get as far a Partition Disks and I get the message "no partitionable disks were found, please check that a hard disk is attached to this machine"

what do i need to do to get the istall to se the new HD?

Thanks, as ever

---

### Post by SilentCacophony on 2005-09-15
Sounds as if you've a problem with the way in which you installed the drive. Usually, you just need to connect the data and power cables, and make sure the jumper is set to master (if it is the only HD.)

Also, I'd check to see if the bois recognises it at all. If not, then it's a hardware problem.

---

### Post by pinbrook on 2005-09-15
[QUOTE=SilentCacophony]Sounds as if you've a problem with the way in which you installed the drive. Usually, you just need to connect the data and power cables, and make sure the jumper is set to master (if it is the only HD.)

Also, I'd check to see if the bois recognises it at all. If not, then it's a hardware problem.[/QUOTE]

with the latitude you just pull the old HD out and pop in  the new one, however F2 setup does not see the HD

---

### Post by leezer3 on 2005-09-15
[QUOTE=pinbrook]I've just popped a new HD into my Dell Notebook, and now tried to install ubuntu from CD (install disk)

I get as far a Partition Disks and I get the message "no partitionable disks were found, please check that a hard disk is attached to this machine"

what do i need to do to get the istall to se the new HD?

Thanks, as ever[/QUOTE]

Hiya,
It did this to me, not quite sure why when I dropped a brand-new 80gb in to replace the 40gb that was in there (Toshiba Tecra S1- Awful machine!). If you're getting errors about being unable to load modules (They all had IDE at some point in), then use a Warty CD to install, and then dist-upgrade either via the internet, or using your CD. 
I've always thought the Ubuntu partioner to be the weakest part of the installer- First there was the CHS vs LBA bug, and now it doesn't recognise my brand-new disk  ](*,) 

Cheers

-Leezer-

---

### Post by pinbrook on 2005-09-15
[QUOTE=leezer3] then use a Warty CD to install, 

-Leezer-[/QUOTE]

Just tried this, with the same result, the install stops at partitioning the disk because it says it can't find the HD


EDIT - I have now returned the HD to the supplier as this seems to be the fault

---

