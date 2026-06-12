---
title: "Installing on machine with Raid array already on machine"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by emustrangler on 2012-06-05
I want to install 10.04 on a Dell Precision T3500.  The machine currently has two HD's set up in a RAID set up.  I don't particularly care, but prefer not to keep the RAID set-up after the install (mainly because I don't want to deal with the added complications during installation of figuring out how to keep the RAID array).  

So my question: is having the two hard-drives in a pre-existing RAID array going to cause problems during the install?  My main reason for worrying about this is that the BIOS has an option regarding RAID.  This makes me think that the hardware is set up somehow to support RAID, and trying to make the two HDs independent is going to cause a mess.

 The options in BIOS are:

1) RAID auto detect/AHCI - RAID if signed drives, otherwise AHCI

2)  RAID auto detect/ATA - RAID if signed drives, otherwise ATA

3) RAID ON = SATA is configured for RAID on every boot.

The third option (RAID ON) is the one currently set.

Auxillary questions: whats the difference between ATA and AHCI?  What's a "signed drive", do I need to "unsign" my drives?

Thanks for any help.

---

### Post by darkod on 2012-06-05
If you are sure you don't want to use them in raid, it's better to delete the meta data first because it can interfere during the install.

I guess the "signed" refers to whether the disks have raid meta data on them or not.

Go into bios first and set the raid to off.
Then boot with the ubuntu cd in live mode (Try Ubuntu), open terminal and remove the meta data from both disks:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

After that, install any way you want.

---

### Post by emustrangler on 2012-06-05
Thanks **darkod**.  I found a Dell start-up utility already installed that removed the metadata, so I didn't need to use dmraid, but other then that, followed your advice and the previous RAID set-up didn't seem to cause any problems.

---

