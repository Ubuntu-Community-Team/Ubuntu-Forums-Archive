---
title: "Server installation with RAID problem"
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by LinuxSpectator on 2013-05-26
Hello,

I encountered two problems during the installation of Ubuntu Server 12.04.
The first problem appeared during the network configuration. The network was successfully configured automatically but the default route could not be determined. The computer was connected to my router via LAN cable all the time. What could go wrong? I regard this problem as minor since I should be possible to setup the default gateway after the installation.

The second problem is crucial. When I try to setup software RAID 1 by partitioning manually, the bootable flags of the physical volume for RAID cannot be turned on (on both devices). Is it the incompatibility of the drives?
I also noticed there is some free space in the beginning and the end on each device which I didn't expect. Is it normal? This is how the partitioning configuration of the first device looks like:
SCSI1 (0,0,0) (sda) - 1.0 TB ATA WDC WD10EFRX-68J
    1.0 MB        FREE SPACE
    #1  4.0 GB      f    swap
    #2    996.2 GB    K    raid
    728.6 kB    FREE SPACE

Appreciate any help.

---

### Post by LinuxSpectator on 2013-05-26
Ok, looks like I've come one step further. After setting up hardware RAID, starting the installation over, failing, disabling hardware RAID, I managed to install Ubuntu server without any errors (except the one with default route) - software RAID1 is configured, bootable flags are on, no partitions with free space and no fatal errors while installing GRUB on the master. My partitions now:

```
SCSI1 (0,0,0) (sda) - 1.0 TB ATA WDC WD10EFRX-68J
    #1   primary    4.0 GB             f             swap
    #2   primary    996.2 GB           K            raid
```

HOWEVER, Ubuntu still doesn't boot and I have no idea why. It might be some entry in the BIOS but which? [This guy]("http://serverfault.com/questions/399286/ubuntu-12-04-cant-boot-after-installing-with-software-raid-1") had a similar problem, but I don't know how to switch to MRB. Anyone??

---

### Post by LinuxSpectator on 2013-05-27
No one?? Not even a hint where to start digging for the cause? Can anyone at least say how I can get some info on GRUB2 settings? I tried it using the ash from the installation CD in the recovery mode but the number of available functions is very very limited :( And I think I've tried out every option in BIOS... It's driving me to despair.

---

### Post by LinuxSpectator on 2013-05-27
GOD BLESS boot-repair AND ITS DEVELOPERS!
There is one thing I am still concerned about though: warnings in the repair boot log file ([http://paste.ubuntu.com/5708210/](http://paste.ubuntu.com/5708210/)). Should I do something about it or the error in the "parted -l" section? It would be nice to get an answer.

---

