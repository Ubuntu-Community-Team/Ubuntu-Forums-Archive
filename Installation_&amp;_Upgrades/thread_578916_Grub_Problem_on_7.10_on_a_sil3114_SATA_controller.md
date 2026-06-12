---
title: "Grub Problem on 7.10 on a sil3114 SATA controller"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Unoid on 2007-10-17
I've searched the forums for a few days and read all the similar style problems.

I have yet figured out how to get this fixed.

My hardware: 
Athlon XP, DFI Nforce 2 Infinity (newest bios), 1gb ddr, 320gb seagate 7200.10
Onboard sata controller is Sil3114 4 port fakeraid. However I am using it for just a bunch of disks.


Upon installation from liveCD gparted recognizes the Hd perfectly. I can install it through the guided partitioning just fine. But when I go to boot for the first time I get Grub error 17.

In my bios I turned the SCSI (sil3114) to SATA instead of SATA-RAID and I still reinstall fresh on unpartitioned hd and get error 18.

I apologize if this was somehow answered before and I missed it while searching.

From what I gather somehow GRUB isn't booting properly or its a MBR problem.

---

### Post by Pumalite on 2007-10-17
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Unoid on 2007-10-17
I appreciate the response and I saw that webpage and tried what it said.

I'll give it another go before asking for more help of course.

Any other possible ideas? Sil3114 doesn't place nice with grub

EDIT:
Question...to fix error 17 it says: 
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)

Since I'm on sata controller should I edit this to , root (sda,1) if thats the drive/partition of the boot?

---

### Post by Pumalite on 2007-10-18
No.

---

### Post by Unoid on 2007-10-20
Very weird. I reinstalled for the 4th time and it finally booted. I havne't done anything else different.

thats not good coding when it'll work once out of 4 cenibus paribus

---

### Post by Pumalite on 2007-10-20
cenibus paribus...ah?

---

### Post by Unoid on 2007-10-23
ceteris paribus - all things equal


thanks for help

---

### Post by Pumalite on 2007-10-23
Condition 'sine qua non'

---

