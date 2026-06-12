---
title: "Upgraded hard drive, second hard drive's LVM no longer auto activated."
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by t-kyle on 2016-01-03
I have two physical drives. One contained OSes and the other data and /home. The second drive contains 2 LVM volume groups. 

I upgraded the OS drive to SSD, copied partitions and all. After the upgrade, Ubuntu would start to boot and then drop to Emergency Mode. I discovered this was because the fstab contained a mount to the LVM on the second drive. If I remove the mount in fstab, Ubuntu boots fine. If I issue a "vgchange -ay" and enter "exit" at the Emergency Mode prompt, Ubuntu continues to load with no problem.

There are 2 symptoms I noticed since the upgrade:
1) Getting to the LVM groups requires manually entering the vgchange command every time.
2) GParted no longer shows the drive as allocated. I thought it would display the 2nd drive as having an LVM volume.

1) How do I have LVM volumes available at startup? I tried a number of things on the web. None worked.
2) Should GParted show LVM volumes?

Note: LVM does not contain boot or root. It's just a data drive. (It will host /home in the future. That's a different project.) The OS is Ubuntu 15.10.

---

### Post by t-kyle on 2016-01-06
Is this the best forum to ask about LVM issues like this? Should I try General Help?

---

