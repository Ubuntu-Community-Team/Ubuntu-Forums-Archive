---
title: "Dual boot preinstallation checklist"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by Pete H on 2005-02-07
I am a newbie to Linux in general and, obviously, to Ubuntu and I wanted to see if I am on the right track.  FDISK list my hard drive as having one primary partition (C drive) and one extended partition (D drive).  Qtparted lists the C Drive as HDA1 and the D Drive as HDA5. Hda5 has over 36 Gb and is empty.  My plan is to do the following:
     1. Remove hda 5 (D Drive) (Fat 32)
     2. Install  two additional primary drives hda5 (again) and hda6.  These will be for        Root and Swap.
      3. Add an extended (logical) partition (hda7) for /home. 

Is this correct?
Should I add additional partitions, such as one for vfat?

Thanks 
Pete H.

---

