---
title: "hard drive is not detected (gutsy)"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Blinkiz on 2007-12-03
Trying to install ubuntu 7.10 desktop edition on my computer but my primary hard drive Western Digital 40GB is not detected.

**Spec**
IDE Primary hard drive. Boots Windows fine.
No IDE Primary Secondary.
IDE Secondary CD-ROM and IDE secondary secondary 320GB hard drive Samsung.
Ubuntu CD burned with old burner at 12x.
The drive is recognized in the BIOS.
gparted under ubuntu 7.10 live cd does not see the drive.
openSUSE 10.2 has been installed on the disk. gparted and all other tools did see the disk from that distro.

**Please advice**

---

### Post by froy02 on 2007-12-03
Some of the  earlier WD hard drives won't configure properly in the bios setup though you see them.  If your bios is capable change the setting to normal rather than auto.
My 25 gb WD hard drive won't recognize a maxtor as slave. it won't be recognized as slave from maxtor nor a 60 gb WD. 
I only buy maxtor and seagate drives now.

Anyway why is your new 320 gb samsung hooked up with the cd-rom.  CD/DVD's can only process data in mode 2, very slow?

---

### Post by klhouse on 2007-12-04
Changing the jumper on my Western Digital from Master to Single solved that problem on my system.

---

### Post by Blinkiz on 2007-12-05
Thanks for the help guys.
Changing the jumper didn't do it for me. I will double check that tomorrow. Setting my other hard drive on the same IDE cable did not work. My old Western Digital wants to be alone :)
> **froy02 said:**
> Anyway why is your new 320 gb samsung hooked up with the cd-rom.  CD/DVD's can only process data in mode 2, very slow?
I thought this had been fixed in newer operatingsystems. Does it still apply? I can't really say that my 320GB hard drive is slow.

---

