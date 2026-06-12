---
title: "Another FakeRAID Post"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Merdril on 2010-06-04
I know you guys are probably fed up with all the posts about FakeRAID (if not, that's even better :)), but I have an interesting issue that I have not been able to find out much about.

I succeeded in *installing* Ubuntu and GRUB, many times, on a FakeRAID array (AMD BIOS Raid v 3.019.somethingsomethingsomething. I can't remember the exact number as I don't have the computer in front of me) running RAID 0. I was able to install Ubuntu 8.04-9.10 successfully, both x86 and x64, and GRUB (I booted into rescue mode off an Ubuntu Server 9.10 x86 and x64 USB to install GRUB and not GRUB 2). To further troubleshoot the issue, I was able to install Debian 5.04 x64 (Only once, we have a bunch of crappy DVD-RWs and it took me forever to find one that was not scratched badly) along with GRUB.

Also, whenever I boot into a live session on my desktop (the problem child) Ubuntu 8.10-10.04 can see the array, see the partitions on the array, edit files on the partitions, chroot into the Ubuntu partition, and save files with no corruption; essentially the live sessions see the array as "normal." So my issue is this: when GRUB loads and I select Ubuntu A.BC, my computer will do one of two things depending on the architecture of Ubuntu. If Ubuntu is x64, the hard drive light will turn on for a brief second, and then the computer will do nothing and the monitor displays a black screen with a cursor blinking at the top. If Ubuntu is x86, the computer will immediately reboot. These two situations occur 100% of the time with no deviation.

I can boot into Windows 7 x64 just fine, so GRUB seems to be functional (on some level) on the FakeRAID 0 array. But Ubuntu will not boot. I checked the menu.lst file to make sure GRUB was pointing to the right device (dev/mapper/pdc_bigafacicf) and partition (dev/mapper/pdc_bigafacicf1) so the configuration seems to have worked correctly. GRUB made no device.map, which, according to the GRUB documentation, means that GRUB had no issue determining the hard drives/array.

Any ideas?

Here's my computer info:
Mobo: ASRock M3A770DE
CPU: AMD Athlon II X4 620
RAM: Patriot G Series "Sector 5" 2 x 2 GB
GFX: Sapphire Radeon HD 5770
HDD: 2 x Western Digital WD5000AAKS (2 x 500 GB) in RAID 0
BIOS device boot order: HDD: RAID Array 1 (that would be the RAID 0 array) -> HDD: RAID Array 2 (that would be a RAID Ready WD 1 TB hard drive) -> HDD: ST136000 (or some number like that, it's a Seagate IDE HDD) -> CD-ROM: Plextor Something

---

### Post by dino99 on 2010-06-04
i've had sometimes ago a system with an Asus card with fakeraid issues using 1 sata and 2 pata (winbond and jmicron chips)

i finally found the solution by plugging hdds in a different order on the board and choosing ahci in the bios.

---

### Post by Merdril on 2010-06-07
Well, this is actually the second raid array on the system, I disbanded the first and built a second in hopes that it would work, but I'll unplug all other drives and see if that works.

---

### Post by Merdril on 2010-06-15
No luck, I even tried reinstalling Ubuntu while all the other drives were disconnected.

---

