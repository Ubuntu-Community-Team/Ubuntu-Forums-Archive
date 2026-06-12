---
title: "Triple Boot: Vista, XP, Unbuntu with Vista installed first"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by someone31988 on 2008-04-26
I'm wanting to triple boot the three OS's and I've come here to ask if the method I'm thinking of will work. Right now I have Vista installed already. I'll shrink the partition down to create an NTFS partition for XP and then an unallocated space for ubuntu to format later. I'll install XP on the new NTFS partition, boot to the Vista DVD to repair the Vista bootloader to be able to boot into Vista again, and then use EasyBCD to add an XP entry to the Vista bootloader. After those two OS's are working fine together, I'll install ubuntu to the unallocated space creating a swap partition and main partition in the mean time. After doing all this, will Grub see the Windows installs and add an entry for each? If not, will it at least see the Vista loader and allow me to chain load Vista or XP after selecting Vista/Longhorn from the Grub menu?

---

### Post by Pumalite on 2008-04-26
That's perfect. Install Ubuntu last and let Grub install to MBR.

---

### Post by Computer Guru on 2008-04-28
> **someone31988 said:**
> After doing all this, will Grub see the Windows installs and add an entry for each? If not, will it at least see the Vista loader and allow me to chain load Vista or XP after selecting Vista/Longhorn from the Grub menu?

It'll most likely add a single entry which will then bring up the Vista boot menu so you can choose which to boot into. 

A better method is to install Windows XP, Windows Vista, Ubuntu then use EasyBCD to add an Ubuntu entry - you'll have one menu with 3 entries.

Install the first two as you would normally (including the EasyBCD part) then install [Ubuntu specifying that]("http://neosmart.net/wiki/display/EBCD/Ubuntu") GRUB should be put in the bootsector. 

Run EasyBCD in Windows to tell it to add a 3rd entry to the Vista bootmenu for Linux. All done.

---

