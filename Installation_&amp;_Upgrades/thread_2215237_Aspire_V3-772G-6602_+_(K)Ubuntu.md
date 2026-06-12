---
title: "Aspire V3-772G-6602 + (K)Ubuntu"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by alucardromero on 2014-04-05
Hello everybody,

Trying to install Kubuntu on to the above mentioned device.  No special hardware has been added.  The laptop comes with Windows 8.  I scrapped it and installed Windows 7 Professional.  I choose "Try Kubuntu..." and I make it all the way to the installer from the desktop and Windows partitions are recognized and reports the whole drive is available, however the partitions are seen in the File Manager.  This issue arises on Ubuntu as well from what I'm reading elsewhere on the forums.

Things to note:

- In BIOS, I have UEFI disabled (Legacy mode), which in turn I believe disables Secure/Fast Boot.
- I installed Windows 7 (plus drivers) in Legacy mode, and I'm able to boot to Kubuntu desktop and use it in LiveCD mode.
- File Manager sees my 100GB Win7 partition, but Installer's partitioner does not, instead reports the whole drive is available.
- There is no RAID setting set from what dmraid states.

I should be able to install, however, I know if I continue to install Kubuntu, I'll essentially be wiping my Win7 partition.  Is there a way around this or to get Kubuntu (or Ubuntu) to read the Windows partition in the partitioner?  I really would like to make this work.  It's a challenge and a headache at the same time.  If you anybody willing to help needs any more information to help come to a resolution, please ask, I WILL provide.

Any help would be greatly appreciated and if you live in El Paso, TX, I will buy you lunch. :P

EDIT: As well, if anybody could point me to the relevant documentation to read if it already exists, I wouldn't mind that at all either. :)

---

### Post by Double.J on 2014-04-05
Hi there!

Can you open a terminal and post the output of 
```
 sudo fdisk -l
```

or on the graphical side, how does gparted see the drive?

If the whole drive is formatted for windows, best shrink it inside windws, not from ubuntu. try using the [diskmgmt]("http://technet.microsoft.com/en-us/magazine/gg309169.aspx") tool.

---

### Post by oldfred on 2014-04-05
If system was UEFI, then you had gpt partitioning.
When you install Windows in BIOS boot mode it converts to MBR(msdos) partitioning but does not do it correctly.
It leaves the backup gpt partition table (one advantage of gpt is a backup of partition table). 
You must delete misc gpt data (backup table) as Linux tools see MBR and backup gpt and do not know what you have or want, so assume you must erase drive.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by alucardromero on 2014-04-05
Thank you to both of you that have responded.  That actually did help out.

Turns out I had GPT signatures lingering, so FixParts actually did help remove that.  After that, it was pretty much smooth sailing from there.  Windows partition was unaffected, as it should be.

Again, thank you very much for the help.  As an I.T. Specialist I'm a little uneducated about UEFI.  I definitely have homework tonight.

;)

---

### Post by oldfred on 2014-04-05
It is possible to install Windows 7 in UEFI boot mode if hardware is UEFI. But you have to convert DVD to flash drive and make some updates to make it UEFI capabile.

---

