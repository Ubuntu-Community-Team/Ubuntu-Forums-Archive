---
title: "Prepare new disk for install? Dual boot from 2 disks?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by AbsolutMayhem on 2007-06-12
Hi everyone. I'm very new to Linux, so please bear with me, and please give me specific (idiot-proof) instructions.

I have a NEC  tablet PC. I bought a new hard drive and want Ubuntu as the OS. I have already formatted the new drive FAT32, but I saw from other posts or instructions that the disk should be empty and not formatted. Can I install with the disk already formatted, or do I need to erase the disk? If it needs to be erased, can you make a suggestion on how to do it? 
 
The internal drive on my pc has Windows XP for Tablet PC loaded. If I connect the new drive (using a USB adapter) and boot, will I be given the option to boot using Ubuntu? I have the option to boot from USB in BIOS - will I need to change the primary boot to USB in order to detect the external disk and boot? If I switch out the drives, can I do this in reverse? In other words, if I have the Linux HDD in the machine and attach the Windows HDD externally, will I be able to boot from Windows? 


Thanks. -L

---

### Post by carcioni on 2007-06-12
With respect to the format of the drive, it won't matter. If you are doing a fresh install, Ubuntu will format it as needed. 

I am not sure about booting from USB, but my suspicion is that the BIOS will just pick up the boot track from the first bootable device it finds, so as long as the USB drive is first in the BIOS boot list, whatever is on the USB drive will boot.

Cheers
D

---

