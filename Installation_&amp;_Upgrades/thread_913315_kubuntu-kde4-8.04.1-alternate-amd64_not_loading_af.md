---
title: "kubuntu-kde4-8.04.1-alternate-amd64 not loading after post-install reboot"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by TDK800 on 2008-09-07
Installed on full disk encrypted volume and after the reboot at the installation it just shows the kubuntu logo and stays loading...

I rebooted with the "rescue" mode kernel where it shows what it's doing and the only error i noticed was:

not found
Setting up cryptographic volume sdb5_crypt (based on /dev/disk/by-uuid/3ee69762-d941-4404-adc1-4be8a4d57c5f)
cryptsetup: Source device /dev/disk/by-uuid/3ee69762-d941-4404-adc1-4be8a4d57c5f not found
Done.
Begin: Waiting for root file system... ...
...
15 lines about initializing the hdd and last line is:

Attached scsi generic sg2 type 0


P.S. I have the hdd connected using SCSI<->USB cable, but I'm not sure if that would cause the problem. more like something missing

---

