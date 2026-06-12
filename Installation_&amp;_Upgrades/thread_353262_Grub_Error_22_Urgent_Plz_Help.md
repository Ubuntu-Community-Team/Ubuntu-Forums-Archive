---
title: "Grub Error 22 Urgent Plz Help"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by CyanEyed on 2007-02-04
HI

i wanted to uninstall ubuntu and give windows my full hard drive (im a gamer, thats the only reason) 
but any way i deleted the linux and linux swap partition. now i cant load, right now im using dapper drake live CD

the error i get is ERROR 22. and using the link in the error 17 thread i got this:

> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

This is the error that people often see after they delete their Linux partition but they still have that partition's Grub's stage1 written in the MBR.

They can easily cure that by overwritting the existing Grub IPL code with code for another bootloader in another operating system.
If no other operating is installed, then installing a new operating system will generally cure this error automatically.

If there is another operating installed in the computer, re-writing the bootloader'e MBR code for that operating system's bootloader and overwriting the now useless Grub code will cure the problem. This can be easily done with Super Grub Disk.
1) Re-install a Grub to MBR from another Linux
2) Re-install a Windows Bootloader to MBR.

but i dont understand it, and i cant get to windows - i need it tommorow at school

how do i fix it??

any help appreciated

thanks

---

### Post by confused57 on 2007-02-04
> **CyanEyed said:**
> HI

i wanted to uninstall ubuntu and give windows my full hard drive (im a gamer, thats the only reason) 
but any way i deleted the linux and linux swap partition. now i cant load, right now im using dapper drake live CD

the error i get is ERROR 22. and using the link in the error 17 thread i got this:



but i dont understand it, and i cant get to windows - i need it tommorow at school

how do i fix it??

any help appreciated

thanks
You need to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)


You can also use the Super Grub Disk to restore it:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

