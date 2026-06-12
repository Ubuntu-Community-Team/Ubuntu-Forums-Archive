---
title: "Can't boot without live USB"
date: 2017-03-14
forum: MINT
---

### Post by jakeb2 on 2017-03-14
my info is at [http://paste2.org/b7vKNBDy](http://paste2.org/b7vKNBDy)

---

### Post by oldfred on 2017-03-14
Moved to Mint sub-forum.

Boot-Repair uses bootinfoscript as part of its report. And that has not been updated to include parsing details of whats in /dev/nvmep1.

Boot-Repair does try to install in BIOS boot mode, grub to MBR of that drive, but shows error.
Error seems related to BIOS not telling operating system that you have nvme drive.
Many have reported with several brands that they had to update UEFI/BIOS so NVMe drive is correctly seen.

You also have a new UEFI system with the very new NVMe SSD drive.
But have installed in the 35 year old BIOS configuration, is that what you intended?

How you boot install media, UEFI or BIOS/CSM is then how it installs.

What brand/model system? Not sure if Mint has all the updates required.

---

