---
title: "Warm boot bios freeze after unbuntu install"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by osbald on 2005-08-03
Hi all, new to the forums and Unbuntu. I've just installed the 64-bit Unbuntu on my new AMD64 machine which dual boots with  the existing XP partition and has GRUB in the MBR. The problem I'm now having is that on a warm boot my machine is hanging in the bios boot-up, its just before the point it'd normally say  "Detecting IDE Drives", when it hangs it also won't allow me to enter the bios settings its just  completly locked-up.

Making matters worse is my power switch dosnt seem to work insofar as cold booting. To get the box running again I've found I need to pull the power cord and wait 30secs, after doing that the bios runs fine, every time. After a session in Unbuntu or Windows XP a restart (or shutdown) will cause the machine to lock-up again.. not much fun especially the first time it happened after the Unbuntu install.. thought it'd destroyed the machine for a gut wrenching few hours until 3am desperately trying to get into the bios to enable cdrom boot (trying and failing).

Any suggestions as to whats going on? hows Unbuntu effecting the bios checks? how do I fix it? would removing GRUB help?

I'm using a AMD64, ASUS AN8 Deluxe mainboard, and SATA HDD (sans RAID). Note Its not getting as far a GRUB, not even liststing drives found. Under a normal run I'd briefly see a list of my DVD, DVDRW & SATA drive found. One other thing that's changed is an unexpected floppy like drive seek noise on boot - when I havn't even installed one (plus its disabled via bios). But I did splash out on a 12-1 multiformat media card reader (attached to an internal usb port), suspect this is making the seek noises but why the sudden problems post Unbuntu? Is it even related to the major problem?

- Richard

---

### Post by osbald on 2005-08-03
Update: I've tried unplugging the media card reader and the problem seems to have gone away. Trouble is I'd like to be able to use the hardware without needing to shutdown and pull the case apart. The reader didnt give me any touble until I'd installed Unbuntu. Anybody know what Unbuntu might be doing to mess up the Bios "Detecting IDE Drives" on a reboot?

---

