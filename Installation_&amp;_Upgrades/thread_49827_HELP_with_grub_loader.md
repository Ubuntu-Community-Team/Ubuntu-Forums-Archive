---
title: "HELP with grub loader"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by Lax D Unit on 2005-07-17
we i finish the first part of the ubuntu instalation it says rebooting into system. then it does and it says starting grub loader then error 21. any idea y it does that . i tried to reinstall it and i tired to install lilo but lilo kept failing to install? thanks for any help

---

### Post by amohanty on 2005-07-18
Do you have multiple hard drives??

AM

---

### Post by Lax D Unit on 2005-07-18
yes i have two IDE hard drives. one is a 120 gig the other is a 14 gig. i want to put linux on the slave drive which is the 14 gig so that means the MBR is gonna be on the 120 gig. does haveing two hardrives mess this up or somthing??

---

### Post by WildTangent on 2005-07-18
[QUOTE=Lax D Unit]yes i have two IDE hard drives. one is a 120 gig the other is a 14 gig. i want to put linux on the slave drive which is the 14 gig so that means the MBR is gonna be on the 120 gig. does haveing two hardrives mess this up or somthing??[/QUOTE]
no, having >1 drive has never given me errors. i might know what the problem is though. some motherboards have a feature that prevents the MBR from being over-written by anything but windows. disable the feature from the BIOS.

-Wild

---

### Post by mingus on 2005-07-18
*grub loader then error 21. any idea y it does that*

*yes i have two IDE hard drives. one is a 120 gig the other is a 14 gig. i want to put linux on the slave drive which is the 14 gig so that means the MBR is gonna be on the 120 gig. does haveing two hardrives mess this up or somthing??*

This error is "selected disk does not exist - this error is returned if the device is not present or recognized by the BIOS."

Does your system's BIOS allow you to set up multiple disks to boot from?

How do you want to manage the dual-boot?  From Windows to Ubuntu?  From Ubuntu to Windows?  From the BIOS?

Do you have a bootable floppy drive?

---

### Post by amohanty on 2005-07-18
> yes i have two IDE hard drives. one is a 120 gig the other is a 14 gig. i want to put linux on the slave drive which is the 14 gig so that means the MBR is gonna be on the 120 gig. does haveing two hardrives mess this up or somthing?? 

No it should not mess things up, I have three of them and it works fine, but try and make sure of the following:

1. In you CMOS make sure that the drives are setup as auto.
    ie. Type=Auto, Mode=Auto for both the primary master and slave drives
2. Make sure your BIOS does not prevent writing to the MBR by non-Win OSs (some wierdo bios' do that)
3. After (1) and (2) reinstall grub to mbr

HTH

AM

---

### Post by Lax D Unit on 2005-07-18
thanks for the help i got it up and running

---

