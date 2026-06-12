---
title: "No EFI System partition"
date: 2024-04-06
forum: Installation &amp; Upgrades
---

### Post by Andrew_McLean on 2024-04-06
Trying to install Ubuntu 22.04 on a new MB, with SSD drive. I get the issue with "No EFI System Partition found".
Have seen various discussions of this issue, but what I don't get is this: why doesn't the installer
have the option "Use the whole disk" ? You used to be able to select this and it would sort out the 
partitioning for you. Now it's asking me to create a suitable partitioning...
AM577

---

### Post by tea for one on 2024-04-06
The Ubuntu installer does have the option "Erase disk and install Ubuntu"
Please see section 6 [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
Section 7 will show that an EFI partition will be created.

A couple of other points (assuming this is a single disk for Ubuntu):-
Boot your live install session in UEFI mode.
Before starting the installer, open Gparted and create a GPT partition table.

---

### Post by oldfred on 2024-04-06
Are you installing to a second drive and using 22.04 or a flavor that still uses the Ubiquity installer.
It has this bug that wants an ESP on the "first" drive. Whatevery UEFI/BIOS calls first drive.
And drive order is most often in motherboard port order so if you put new drive in higher numbered port is may not be first drive.

 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I always change drive to gpt (starting in 2010 on new drives) and add an ESP (starting in about 2013) as first partition even for data only drives. I typically like a small install for emergency boot even on large data drives. Did not have UEFI system until 2014 and had to have a bios_grub partition to boot in BIOS mode from gpt.

---

### Post by Andrew_McLean on 2024-04-08
Thanks for the tips. My fault entirely - I eventually realised that when reassembling my PC I had not connected the power cable to the SSD, So there was only the USB
from which I had booted up,  and when the U. installer got to the point of looking where to install, it just showed me the partition map of the USB. It would have helped if it had said something like "You appear to be planning to install Ubuntu onto the USB from which you just booted...this seems odd / stupid / probably not what you want,,,".
Or even just "Where's your HDD ?"
I also noted that the BIOS display of my new MSI MB has a display of the storage (e.g. 8 SATA ports), but that is tucked away on the 'alternative' display, not on the main one.
Anyway, I made some notes for next time...!

---

