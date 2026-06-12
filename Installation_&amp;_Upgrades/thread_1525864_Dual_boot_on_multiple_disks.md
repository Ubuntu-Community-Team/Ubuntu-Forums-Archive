---
title: "Dual boot on multiple disks"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by rsvr85 on 2010-07-07
Hey everyone.

I recently tried installing Lucid x86 on my system beside Windows 7 and managed to screw it up.

My disk setup is this;

Disk A = 3 partitions (1st partition=Windows 2&3 partitions=Data)
Disk B = 1 partition
Disk C = 3 partitions (1st partition=Data 2&3 partitions=Ubuntu & Swap)

Disk A = SATA and internal
Disk B = SATA to USB external
Disk C = SATA to USB external

I want to install Lucid on the 2nd partition on Disk C.  And dual boot it with Windows on Disk A.

During Lucid setup i specified the partition for installation (C2) and asked for GRUB to install on Disk A (no partition specified) so GRUB is always used as the dual-boot manager even if the Lucid disk (Disk C) is ejected.
Once installed and rebooted i was taken to the GRUB rescue prompt as no installation drive could be found (a long string of numbers (looked like a Disk ID number???) was also shown).  Obvviiusly, i could not access either OS on my system at this point.
I had my W7 DVD handy so it was just a case of recovering the windows boot manager and i could use my PC but how do i go about installing Lucid with this setup??  Should i specify a partition for GRUB to install to?  I have a hunch this is where i am going wrong but am too scared to try again and potentially balls things up.
TIA for any help! :D

---

### Post by tommcd on 2010-07-07
> **rsvr85 said:**
> 
During Lucid setup i specified the partition for installation (C2) and asked for GRUB to install on Disk A (no partition specified) so GRUB is always used as the dual-boot manager even if the Lucid disk (Disk C) is ejected.

If you want grub2 to control the booting of Ubuntu and Windows, you can boot from the Ubuntu live CD and install grub2 to the MBR of "Disk A" (note: this will be /dev/sda in linux) like this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just try the first method listed there.
Also, make sure that "Disk A" (dev/sda) is set as the *first boot device* in the computer's BIOS.
Also note that, if you want Ubuntu's grub to control the booting of your computer, the external drive will have to be connected to the computer for this to work properly.

---

### Post by rsvr85 on 2010-07-07
Hi tommcd, thank you for your reply an the links :)

My BIOS was set correctly and i installed GRUB straight to Disk A as per the instructions.

Is there no work around to get GRUB working without Disk C on the system.  I understand that without the Ubuntu install present it will not boot but can GRUB not still be used to select Windows?

---

### Post by tommcd on 2010-07-07
> **rsvr85 said:**
> 
Is there no work around to get GRUB working without Disk C on the system.  I understand that without the Ubuntu install present it will not boot but can GRUB not still be used to select Windows?
As I understand it, the grub2 needs to refer to the grub configuration files in your Ubuntu's /boot/grub/ directory. Also, the files in /etc/grub.d/, and /etc/default/grub file need to be available as well.
So if you don't want to have the Ubuntu external drive connected all the time, you will need to look into alternative boot managers to boot both Ubuntu and Windows.
I am not familiar with these though.

---

