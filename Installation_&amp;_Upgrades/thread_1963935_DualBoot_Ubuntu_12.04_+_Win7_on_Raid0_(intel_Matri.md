---
title: "DualBoot Ubuntu 12.04 + Win7 on Raid0 (intel Matrix Storage)"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by RoNnie9ita on 2012-04-23
Hi to all, 
i have a problem, my new pc is configured with:
intel i7
asus p7h57d-v evo
16gb ddr3 
ati hd5670 1gb ddr5
2x320gb (raid0)
2x1tb (raid1)

at this moment i have installed only win7 and i run ubuntu on virtualbox, but i would to try ubuntu in a real installation on the disk.

when i istall ubuntu, it give to me an error on grub's installation on the raid disk.
i've also tryed also linux mint 12 and ubuntu 11.10.
what can i do for this problem?

i've read many thread but without a solution...

help me...
and sorry for my bad english :S

---

### Post by darkod on 2012-04-23
If you use the standard live cd for installation on fakeraid, the grub2 install frequently fails.

If you finished the install and only grub2 is missing, there is a way to add it.

Or another option is to do a new install with the alternate install cd, that is the cd that needs to be used for raid installations.

---

### Post by RoNnie9ita on 2012-04-23
yeahhhh thank youuuu i've tried with alternate cd and after an initial error on the grub's installation ... all is gone fine.

Now... ubuntu it's ok and my pc start with grub from the raid0 THANK YOU!!! ;)

- the installation is gone fine only with OEM setup... not with normal... ;)

---

