---
title: "Install Ubuntu on UEFI system"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by bill-lancaster on 2013-01-05
Having (temporarily) given up trying to install Ubuntu alongside Win 8 I tried a) removing hard drive with win 8, replacing it with a drive without an o/s.

I had a Ubuntu 12.10 64 bit in the drive.

I got to a screen saying "select boot device" with several options that I didn't really understand.  I chose "UEFU hp cd..."
DVD drive busy for a while, blue screen and that's it.

I think I need to use the WUBI installer which I have downloaded.  If this is the case, how should I proceed?

Thanks to all for their help sofar.

---

### Post by dorruk on 2013-01-05
First consider checking out whether you are on UEFI or Legacy boot from BIOS. If on UEFI, then follow installing Ubuntu on UEFI:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If Ubuntu is already installed and is a stand-alone OS in the drive, then consider making a Boot-Repair disk:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-01-05
Wubi does not work with gpt partitions, and since Windows 8 pre-installed uses UEFI secure boot, you cannot use wubi. 

+1 on info from dorruk

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.

Systems need quick boot or fast boot turned off in UEFI settings, and some systems with Quick Boot on and Ubuntu booting could not get back into UEFI menu.

---

