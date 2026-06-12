---
title: "Dual boot with Windows 8"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by garryhughes on 2013-08-17
I've installed Ubuntu many times, but never with Windows 8. My concern is the uefi boot situation, which I know nothing about.

I have windows 8 installed on a 128gb SSD.
I have a separate HDD, 3TB, and I intend to partition part of this drive to install Ubuntu.

Questions:

How can I tell if my boot setup is UEFI?
How much space should I allocate to Ubuntu?
What's the best install method (surely a current how to exists?).

I've tried to google this, but I'm still not sure.

Thanks in advance for any advice.

---

### Post by grimm2 on 2013-08-17
your definitely smarter as me , ive tried it and i can't get it running , check the thread one up of you (atm) 
[http://ubuntuforums.org/showthread.php?t=2168291](http://ubuntuforums.org/showthread.php?t=2168291)

---

### Post by oldfred on 2013-08-17
If Windows was pre-installed it is UEFI. If user installed it probably is BIOS.
A UEFI install uses gpt and has the first (or often second with Windows) partition as the efi partition.
BIOS installs use MBR(msdos) partition with Windows. With MBR partitioning both Windows & Ubuntu have to boot with BIOS.
Ubuntu can use gpt partitioning with BIOS if you have a bios_grub partition or UEFI if you have a efi partition.
To easily dual boot both systems must be either BIOS or both UEFI. New UEFI systems have CSM which is compatiblity with old BIOS configurations.
How you boot, UEFI or BIOS, the install media or flash drive is how it installs.

Post this to see partition type:
       sudo parted /dev/sda unit s print

 sudo parted /dev/sdb unit s print

---

