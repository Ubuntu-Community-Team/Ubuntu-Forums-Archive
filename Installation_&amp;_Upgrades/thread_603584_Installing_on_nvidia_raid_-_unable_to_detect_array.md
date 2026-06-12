---
title: "Installing on nvidia raid - unable to detect array"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by azzido on 2007-11-05
I'm using a nForce 4 based motherboard. I'm running two disks in a raid 0 configuration on the nvidia based raidcontroller. There is another raidcontroller on the motherboard, but the nvidia one is the only one with S-ATA 2.

My problem is that Ubuntu detects the disks, but not the array. I've checked some other posts, but there very little information out there. They suggest that nvraid (nvidia raid) isn't a true hardware raidcontroller, and I need to look up on some softwarebased raidsetup for linux.

For the record, I'm running three primary partitions on the array (raid0 disks).
1: - Windows Vista
2: - Reserved for a linux distro (pref. Ubuntu -_-)
3: - Storage

My wish is to setup Ubuntu to detect the current array, and install Ubuntu on the reserved partition. What I don't wish is to break the array up. If Vista detects the raid without problems, then Ubuntu should too. Now I know software development on this platform is very much based on the grace of voulenteers (and not to mention manufacturers), so abit of fiddeling myself can be accepted :) 

I hope you guys can offer me some advice, else I might have to switch to a single disk configuration, and that would be loss to me and the linux world. Atm, theres no danger if the array gets broken or destroyed, so I would like to try it before I have something that cant be deleted.

---

### Post by psusi on 2007-11-08
See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

