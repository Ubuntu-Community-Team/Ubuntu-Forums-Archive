---
title: "Can't install on Abit SG-95 motherboard"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by nigeldodd on 2007-01-20
I have tried 6.10, 6.06 combined with  both i386 and 64 bit distros and the alternative instalation disks and the results are pretty much the same with all of them.

The main issue I have is that the installation process cannot see the Sata drive I have. When I add a conventional IDE drive the installation process can see the drive but it cannot format it or seem to be able to access it except to tell me its size and make. 

The motherboard is an Abit SG95 which hosts socket 775 cpu's. The motherboard has built-in ethernet, graphics, sound. These use Sis chipsets. 

The Sis ethernet is not detected by the installation process which is another problem. But the main problem is disk access, even the old IDE ones. Impossible to move forward without this!

Nigel

---

### Post by nigeldodd on 2007-01-21
By disabling the on-board Ethernet driver I have been able to install 6.10 64-bit on the second ide drive. 

However I still can't see the SATA drive at all.

I should mention that Windose can see all three drives (the first IDE on which it is installed, the second IDE on which Linux is now installed and the SATA drive, 320Gb, all currently formatted as FAT32).

I really need to access the SATA drive from Linux if this is to be a viable system. The motherboard, an Abit SG95, has no bios update issued by Abit. Are there SATA modules for Ubuntu that can be obtained? How should I proceed?

Nigel

---

### Post by nigeldodd on 2007-02-14
To conclude this thread, I have given up trying to get this motherboard to work with Linux and a SATA drive. 

I put the SATA drive in my other machine and it is seen by Ubuntu.

I shall buy another PATA drive for the new AG-95 machine and not use Abit motherboards again. Technical Support says they only support Windose.

---

### Post by ffxr on 2007-02-25
did you check the SIS site? they have kernel patches for the SATA & RAID controllers (amongst other things) for this board..  if you are confident enough to install these and they work, can you let me know..? i have the same board and i am considering installing some of these kernel patches.. but i have to do a little bit of research/reading up first , in case i break my system... thanks

---

