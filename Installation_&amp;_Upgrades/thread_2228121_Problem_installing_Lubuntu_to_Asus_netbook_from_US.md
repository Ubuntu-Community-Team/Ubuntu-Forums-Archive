---
title: "Problem installing Lubuntu to Asus netbook from USB flash drive"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by alex.mardigian on 2014-06-05
I recently bought an Asus Eee PC 1025c-m17 and I want to install Lubuntu (or some Ubuntu variant).  I tried installing it via a bootable USB flash drive with lubuntu 12.04 and 14.04 on it, but the machine still boots into windows.  After going into bios to set the boot order, the only 2 options I see are:

1. Sata PM: WD3200BPVT-80JJ5  (hard drive)
2. UEFI:  PAMP

There is no option for removable storage.

I tried updating the bios to the latest version.  I've tried downgrading the bios to a previous version.  Still, no (recognizable) option to boot off of a usb flash drive.

Here are the specs for the Asus Eee PC 1025c:

Processor:  Intel Atom N2600 1.60GHz
Memory:     1 GB
Harddrive:  320GB
32-bit OS

Has anyone else encountered not having "Removable Storage" as an option to boot from, in a netbook?  If so, how does one get around this?

---

### Post by Rex Bouwense on 2014-06-05
I also have an ASUS EeePC and if you look at the BIOS again you will see a + sign by the hard drive.  For some reason some computers recognize a USB Flash Drive as another hard drive.  Mine is one of those so in the BIOS, navigate to boot and then to the hard drive.  If you hit enter and you see your flash drive under hard drives, you know that your computer also falls within that group.  Simply move the flash drive to the top of the list.  Save, exit, and continue to boot.

---

### Post by alex.mardigian on 2014-06-06
That worked!  Your advice lead me down the right path to the solution!

Although I did not see a + sign by the hard drive, the hard drive did have the option 'PMAP' (instead of 'Removable Storage' or 'USB' or something similar).  So, I changed it from "Sata PM: WD3200BPVT-80JJ5" to "PMAP" and that worked.

I will post some pictures of what exactly was changed where (in bios), soon.  Just to be more clear for someone else who has (or will have) the same problem.

Thanks for the tip, Rex!

---

### Post by mörgæs on 2014-06-06
Good, please mark the thread 'solved'.

---

