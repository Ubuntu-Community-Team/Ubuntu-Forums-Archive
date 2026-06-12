---
title: "Grub using IDE and SATA issues"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by PiRho on 2010-08-01
I have tried to install ubuntu onto my computer using the live CD.  It installed fine, and it put grub on sda (which linux sees as my SATA drive.  Windows is installed on the ide drive which linux see's as the sdb drive.  It was a successful install and in theory it should work, except it find the windows install first so it boots into windows without using grub.  

I think that linux assigns the drives using the sata first and the ide second, but windows does the opposite and the ide drive is first and the sata is second.  Is it possible to install grub onto the ide drive and get it to dual boot linux or is it possible to use the windows bootloader to recognize the linux install and chainload grub?

I am thinking that if I use grub on the ide drive it will throw an error like what happened during my wubi install and it is unable to find the kernel because it is looking for it on sda, but from a windows install it is sdb.  I have tried to get the computer to boot from the sata drive, but the mobo is a bit old and I do not think it is supported.

Thanks

-Jeff

---

### Post by oldfred on 2010-08-01
Since your BIOS supports both SATA & PATA drives can you choose which drive is the boot drive. If so just change boot drive. It is usually separate from the choice in BIOS of boot device - HD, CD, floppy etc.

If not, you can install grub to sdb and it should boot as it really uses the UUIDs, set root is just a start point on boot so if drive number is wrong it will still try to find it by UUID. So it usually works.

---

### Post by PiRho on 2010-08-01
Yeah I had tried setting it to boot off of the SCSI (as it calls the sata) in the bios but it didnt work.  Instead if I select scsi from hitting f9 then it does work.  Ahh  that works well enough for me no need to mess with grub or the windows bootloader seeing as they are on different drives.  I can keep them completely separate.

---

