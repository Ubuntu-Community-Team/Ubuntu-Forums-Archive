---
title: "dual booting Xp with Ubuntu"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by PhoenixVarga on 2011-09-16
Hi. I'm trying to install both Xp and ubuntu on the same HDD.

I had to disable the SATA native mode in order for the Windows CD to recognize my HDD. I created only 1 partition and installed. 

Windows ran perfectly.

Then I used a live CD of Ubuntu 10.04 and ordered it to install it side by side.

Installation ran fine.

But when It restarted spit me directly to grub rescue telling me no partition was found...

I checked my partitions with ls and I have only hd0 and hd0,1

I've looked for hd0,1/boot/grub or anything but it says unknown filesystem

I've even wiped out XP and installed only ubuntu and the same things happen.

I also used the exact same live CD on another different HDD to install ubuntu and it did work perfectly


any ideas?

---

### Post by Hakunka-Matata on 2011-09-16
Hi, Welcome,

Please post the output of 
```
sudo sfdisk -luB
sudo fdisk -lu
```

---

