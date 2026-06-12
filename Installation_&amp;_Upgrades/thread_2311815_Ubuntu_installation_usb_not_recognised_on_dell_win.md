---
title: "Ubuntu installation usb not recognised on dell windows8"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by Shibaji_Saha on 2016-01-30
Please help!!

i have been trying to replace windows 8 on my dell Inspiron desktop for the last week and failing miserably!

i have disabled secure boot option. But whenever I try booting with the ubuntu usb it boots windows. 

I have now changed the boot device to only usb. When I try booting with usb as the only option to boot it says 

'no boot device available'
SATA 0 Installed
SATA 1 None
SATA 2 installed
SATA 3 None

i just cannot get the machine to boot from the usb!

---

### Post by yancek on 2016-01-30
What software did you use to create the bootable usb drive with Ubuntu?
Did you do an md5 checksum on the downloaded iso to verify it?
Generally upon entering the BIOS, you will see a number of tabs, one of which is Boot.  You need to look somewhere in there where you can set the priority to boot.  What you show are all SATA drives which are not usb.  You might check the manual of your computer to see how you can set boot priority.  If you have windows 8 using UEFI, make sure you install Ubuntu using UEFI also.

---

### Post by ubfan1 on 2016-01-30
And on some machines, setting a supervisor password will enable other boot choices, like "UEFI USB".

---

