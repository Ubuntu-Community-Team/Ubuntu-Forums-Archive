---
title: "Boot failure after removing internal hard drives"
date: 2022-11-27
forum: Installation &amp; Upgrades
---

### Post by padge01 on 2022-11-27
Hello all, 
After a series of unfortunate events I had almost restored my desktop to usable, but again ran into a boot error. 

I recently installed a new NVMe SSD and attempted to clone my old SSD with Windows 10 to it. Somehow the clone failed and either of the SSD's would not boot to windows. I tried to repair windows install as well as fresh installs for a while before giving up due to failure errors and instead installed a fresh version of Ubuntu 22 on the clean NVMe drive. 

Before this install the older 1 and 2tb hard disk in the desktop were giving issues, the 2tb disk was reporting uninitialized even in windows 10 (computer hadn't been turned on for several months and disk was uninitialized on reopening) and the 1tb disk was reporting itself as unpartitioned to Ubuntu and I had to perform a file recovery to get old files back. 

Today I removed both the internal hard disks so now the only disks in the computer are the original SSD with old and broken windows 10 install, and the new NVMe with the Ubuntu install. But immediately after removing the two  other disks Ubuntu fails to boot and asks me to insert a bootable media. 

I opened a trial of Ubuntu from the install usb and ran boot-repair. Below is the paste bin output from boot-repair 

[https://paste.ubuntu.com/p/MsnD5FsjSP/](https://paste.ubuntu.com/p/MsnD5FsjSP/)

I'm not sure how to address this error from when I attempt repair
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."
and I'm nervous to wipe either SSD to clean install Ubuntu again as the files from my other disk are saved in a recovery directory of the Ubuntu install of the NVMe disk that is now failing to boot. 

Before I removed the two internal drives there was an error occuring during startup about a disk failing to load, but after displaying this for a while it would boot into Ubuntu and allow me to view all the disks except the uninitialized 2tb. 

All and any help appreciated, in over my head a little. 

Thank you

---

### Post by tea for one on 2022-11-28
> **padge01 said:**
>  I'm nervous to wipe either SSD to clean install Ubuntu again as the files from my other disk are saved in a recovery directory of the Ubuntu install of the NVMe disk that is now failing to boot.
I think that your first priority is to backup Ubuntu and Windows personal data on a disk where you do _not_ want to install an OS.
Then, when re-installing or fixing boot problems, your backup is not compromised.
> I recently installed a new NVMe SSD and attempted to clone my old SSD with Windows 10 to it. Somehow the clone failed and either of the SSD's would not boot to windows.
Windows is often tied to hardware and cloning need extra attention. Windows forums are probably better suited to offer current advice.

Boot-repair [COLOR="#0000FF"]line 266[/COLOR] - LegacyWindows detected. The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
The modern way is to install Windows 10 (and Ubuntu) in UEFI mode with GPT.
Here is some info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Anyway, organise your data backup first and then we can try and help with OS installation(s).

As you have multiple disks, each OS on a separate disk is preferable.
Many users (myself included) only install Ubuntu and then use Windows 10 in a VM - worth consideration?

---

### Post by padge01 on 2022-11-29
Thank you for the reply. I realized that my grub boot loader had been installed on a partition on the disk I removed (an issue I found mentioned elsewhere with Ubuntu installs), and I ended up deleting all rogue partitions, disconnected all disks except the target one and reinstalling Ubuntu fresh.

---

