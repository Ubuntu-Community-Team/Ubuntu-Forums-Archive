---
title: "Installation on SATA drive, disk not found after boot"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by purplecow on 2008-04-18
I have a problem booting from a SATA-drive. Installation for ubuntu 8.04 went smoothly, but the computer won't boot from the drive, it tells me to "insert system disk and press any key".
If I boot with the livecd and choose "boot from first hard disk" I get to the grub menu, where I can pick the ubuntu installation and then it starts up just fine.
I also have vista installed on another partition. It won't boot from the grub menu, nor will it boot if it is the only operating system on the disk.

I am able to boot he computer from either the dvd-drive or from a PATA-drive. I have tried switching boot priorities around in BIOS, and tried disconnecting all other drives from the computer.

The motherboard is a Abit I-45CV, it uses the Intel 945GC / ICH7 chipset. All the hard disks seem to function perfectly, as ubuntu finds them all and I can access the files. Any help is appreciated, I'm really stumped with this. Of course I could just put the OS'es on the PATA drive, but that would be running away from the problem.

---

### Post by Pumalite on 2008-04-18
If you use Vista, you have to partition with Vista partitioner. You cannot partition with Ubuntu CD

---

### Post by purplecow on 2008-04-18
I partitioned it in two halves with the vista partitioner, then installed vista on it - wouldn't boot. Tried again, still nothing.
After that I put ubuntu on the unpartitioned half, with this limited success.

---

### Post by Pumalite on 2008-04-18
Better to install Vista in the whole drive, then 'shrink' it, giving space for Ubuntu.

---

### Post by purplecow on 2008-04-20
I moved the drive from SATA1 to SATA3 on the motherboard and now it boots into GRUB without a cd in the drive. Ubuntu boots up ok from the menu, but vista still complains from a disk error.
I'm going to try installing vista again, seems like it has issues.

---

### Post by Pumalite on 2008-04-20
That's M$ for you!

---

