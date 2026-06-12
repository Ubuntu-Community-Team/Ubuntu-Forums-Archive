---
title: "cannot disable fakeraid on installation"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by grimreaper80 on 2011-07-31
Hello,

i wanted to install Ubuntu 11.04 on my pc (dual boot with windows xp which is already installed on one disk). 
I have a Asus P5K pro (motherboard) which has a integrated raid controller and i have two 500 GB hard disks.
On BIOS raid is disabled. On Windows i see 2 different disks (correctly).. 
When i try to install Ubuntu, on the disk/partition stagei only see /dev/mapper/xxxxxx which should be the raid (i could be wrong). I tried booting inserting the nodmraid option but if i do i cannot see any disk. 

what can i do to solve this?

Thanks,

---

### Post by YesWeCan on 2011-07-31
There are metatdata blocks on your disks that Ubuntu is probably detecting and therefore assuming they are still components of a Windows RAID. To remove them:
[COLOR="Navy"]sudo dmraid -E -r /dev/sdn[/COLOR]   where n is the drive letter

---

### Post by grimreaper80 on 2011-07-31
Hello YesWeCan,

thanks for your prompt reply. I just tried what you advised and worked great.

Thanks!

---

### Post by YesWeCan on 2011-07-31
Pleasure. Would you mind marking this as solved in the **[COLOR="Red"]thread tools[/COLOR]** menu?

---

