---
title: "Mylex Flashpoint BT-950, no boot after 8.04 to 10.04 upgrade"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by andrew_ioc on 2010-11-01
I've an old backup mail server that was running 8.04 LTS from a couple of SCSI drives connected via a Mylex BT-950 Flashpoint PCI card. I upgraded interactively to 10.04 LTS and now the system doesn't boot, it drops into ash after giving the Gave up waiting for root device... messages. It looks like the newer Ubuntu doesn't see the hard drives at all, and when I thought to use dmesg in the shell I found a number of BusLogic: ... messages saying that Flashpoint support was omitted in the kernel.

When I booted from the 10.4 Desktop CD as if I was going to install the partition editor didn't show the SCSI drives.

This box also has an Adaptec 2940 SCSI card in it. Was Ubuntu confused by the 2 different SCSI cards? Is there anything worth my trying, or should I pull out the 8.04 CD and reinstall the old OS?

Andrew

---

