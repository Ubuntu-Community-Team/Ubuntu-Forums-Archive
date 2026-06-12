---
title: "Dual boot with Windows XP"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by GRobLewis on 2011-09-30
(This occasional Windows user is shaking his head at what would be so simple with a Mac…)

Someone gave me an old Dell PC with XP. Since the motherboard had unused SATA ports, I added a 500GB SATA drive next to the original IDE drive, thinking I'd use it to boot both ubuntu and a clone of the original drive's Windows installation. 

I've gotten as far as creating a NTFS partition on the new drive and cloning the file system from the old IDE drive to it (using Parted Magic). Now I'm stuck trying to figure out how to get the system to boot from the new drive. The BIOS setup doesn't even offer the SATA drive as a boot option. 

So 2 questions, really: 

1. How do I convince the machine to boot Windows from the new drive? When I boot from the original drive, the SATA partition does show up in Windows Explorer. 

2. If I'm able to do that, how do I then create an ubuntu partition on the new drive and have the option to boot either it or Windows?

---

### Post by Hakunka-Matata on 2011-09-30
Mixed drive types: IDE/PATA & SATA
You may want to check the jumper settings on the IDE/PATA drive.  Set the IDE drive jumpers to Master, if not already set to that.  If that doesn't help finding the SATA drive in BIOS, you could simply disconnect the IDE drive and see if SATA drive shows up.
(probably not necessary to mention, but....) Older BIOS choices often include a HARD DRIVES settings, where the drive to get booted is the drive selected in the HARD DRIVE section of BIOS.  And also of course then the first boot device should be HARD DRIVE.

---

### Post by GRobLewis on 2011-09-30
> **Hakunka-Matata said:**
> Mixed drive types: IDE/PATA & SATA
You may want to check the jumper settings on the IDE/PATA drive.  Set the IDE drive jumpers to Master, if not already set to that.  If that doesn't help finding the SATA drive in BIOS, you could simply disconnect the IDE drive and see if SATA drive shows up.
(probably not necessary to mention, but....) Older BIOS choices often include a HARD DRIVES settings, where the drive to get booted is the drive selected in the HARD DRIVE section of BIOS.  And also of course then the first boot device should be HARD DRIVE.

Thanks for your thoughts. But...
--The PATA drive is already jumpered as Master, I'm pretty sure (either that or it's on Cable Select and is the Master). 
--I connected the SATA drive to the SATA 1 port on the motherboard, not SATA 0, specifically to try to avoid any potential conflict with IDE drive numbering. 
--The BIOS definitely sees the SATA drive, it just doesn't offer it as a boot option. (I'm out of my depth here, but I think that disk partitions have a "boot" flag, and as of now the SATA Windows partition does not have it set. Could this be why the BIOS doesn't offer it as a boot option? I think I could use Parted Magic to set that flag if need be.) 

I looked at the Windows boot.ini file but have no idea what, if anything, to change in it.

---

### Post by oldfred on 2011-09-30
Boot flag is not used by BIOS except for a few Intel motherboard that will not let you boot without a flag. Grub does not need one, Windows has to have it on a primary partition to know what partition to boot or repair.

I do not know Dell computers, but one user I was helping had an early Dell with IDE & one SATA port. It could only boot from IDE drive, we never seemed to find a setting to change to SATA to boot. Normally any BIOS that has SATA has to have a BIOS setting as the drive has no jumpers.

Do you have a boot loader in the MBR. With flash drives a BIOS will not present it to boot unless it is bootable. But most newer BIOS let you set SATA drive before you install anything.

Or you may only be able to boot from IDE drive. if so put grub2's boot loader in sda (IDE drive) and use it just for booting.

---

