---
title: "Install Complete failure"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by Cufishing on 2005-10-26
This is a very long post! It is written in three areas.
1. Hardware 
2. Phase I trial and failure.
3. Phase II trial and failure.

Ok, custom rig, MSI MB nVidia nForce 2 chipset, 1GB DDR, HDD-0. WD 120GB ATA 100, HDD-1 WD 100 ATA 66. CD/RW. ATI 9600XT. TFT 19".

Ubuntu 5.10 .iso burned to cd-r.

Phase I:   Primary WinXp drive phyiscally removed, small spare drive replaced as HDD-0.
Everything goes just fine, until the reboot.
At reboot, = Disk Failure, insert system disk, yada, yada.

Ok, boot back into WinXp, and check the small HDD, everthing formated as was described by installer, all 3 partitions present etc.


Phase II:   Left primary WinXp drive in place. Used small drive as HDD-1 for Ubuntu install, again evrything went as well as expected. This time install asked to install 'Grub' into boot sector of HDD-0. I allowed, and things finished, drive ejected CD, remove for re-boot. Ok, re-boot. 
Loading install 1.5
error
Grub failure:
error 21.

At this point, I booted WinXp cd and 'fixmbr' on HDD-0, and booted back into my WinXp. HDD-1 looks just like it should, 3 partitons, LVm etc.

The small drive is good, as I loaded a quick (ha-ha) Win OS to ensure it was good.

At this point, I'm asking for HELP.
My system is back as WinXP, HDD-0 WD 120, HDD-1 WD 100, CD/RW.

---

### Post by Cufishing on 2005-10-26
Bump

---

### Post by Koybe on 2005-10-26
I got this on the Grub Manual page :
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

But i have no idea on what to do. Maybe you can try by installing grub on another HD, and modifie the c:\boot.ini file to get on the linux partitions.

---

### Post by Cufishing on 2005-10-26
Bingo!
Than you so much. BIOS memory did hold the old values, therby the disk was non-existent in BIOS, but fully available under the OS.
I'm up and running.

---

