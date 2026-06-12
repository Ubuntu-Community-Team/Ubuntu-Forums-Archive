---
title: "problems ubuntu starting up - dual boot with winXP - raid set"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by hlpsmb on 2007-01-19
Hello,

OK, I have an asus A7V333 motherboard and have installed a PCI to SCSI RAID card, so that there are two hard drives attached to the card - 1. Primary Master 2. Secondary Master. The two are paired as a mirrored set and I have had them configured this way for a few years running winXP only. With windows the set is invisible to the OS, so the mirroring appears seemless.

I have a third harddisk, attached to the Primary IDE motherboard slot - Primary Master.

Upon boot up the bios is set to scsi so that windows boots from the RAID card not the motherboard.

I downloaded the Ubuntu CD 6.06 and installed it to the third harddisk, allowing it to repartition the whole drive as it wanted. It then downloaded about 170MB of updates and installed them.
Grub was installed - to what appears to be the first harddrive in the RAID set.
Upon reboot this caused a failure within Grub itself so I could not load niether windows or ubuntu.
I went into the RAID configuration and removed the set pair, so that the two disks are no longer mirrored but seperate. This then allowed grub to run and gave the option of running either ubuntu or the two windows OS's (one on each of the previous mirrored pair).

I can successfully go into both Windows OS's - but can no longer get Ubuntu to run.
If I select Ubuntu from Grub, it starts Ubuntu running, so it seems to be pointing to the right place, but when Linux starts it bombs out with statements saying the it cannot MOUNT /dev/hde1 on root, plus mount /root/dev, /sys, and /proc.

I would assume this is related to the RAID set no longer being present? As ubuntu was installed with the RAID set, but then I had to delete the set to get Grub to run.

Any ideas on how to fix this please? I am not Linux savvy so as much detail as possible would be most helpful.

Thanks very much,
Shane

PS. Ideally I would like to have the RAID set working again along with Ubuntu on the seperate drive, but if this is not possible, then so be it. I knew I was taking a punt, but then life would be boring if we don't take risks :)

---

### Post by hlpsmb on 2007-01-20
Anyone?

Is there a file within ubuntu that I can edit to ensure that Linux gets mounted to the correct disk and partitions?

HELP!!!!!!! please  :-)

---

