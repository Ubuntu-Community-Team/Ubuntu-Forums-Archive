---
title: "Boot-Repair not helping"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by adam121 on 2015-02-14
Hi guys just installed newest Ubuntu on my pre installed with Win8 Alienware M17R5.
But after rebooting Ubuntu pop in automatically with no options or Grub menu what so ever.
Tried Boot-Repair but after that have Grub menu with Ubuntu options only.
Here is my pastebin from Boot-Repair

[http://paste.ubuntu.com/10222932/](http://paste.ubuntu.com/10222932/)

also can not access my widnows partitions - read only when mounting don't know if this is the issue
Thanks

---

### Post by oldfred on 2015-02-14
Pre-Installed Windows use UEFI with gpt partitioning. And Windows only boots in UEFI mode on a gpt partitioned drive.
But you have installed Ubuntu in BIOS boot mode.
UEFI and BIOS are not compatible and you must reboot and in UEFI menu choose boot mode first. With some systems you may in UEFI have to turn on/off UEFI or CSM/BIOS boot mode also.

Only systems installed in the same boot mode as Ubuntu/grub will work from grub menu.

You now are not showing the efi partition which must be FAT32 and with boot flag. Did you overwrite that with the bios_grub partition?  Normally the bios_grub partition is only one or two MB. If so core.img overwrote some of your Windows efi boot files and it is probably not recoverable. You will have to use your Windows repair disk to restore the Windows boot files after creating the efi partition.

You also do not seem to show the system reserved partition.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

And you left Windows hibernated or its fast boot setting turned on. That makes it difficult to dual boot and get into Windows even just to make repairs.

You need to install Ubuntu in UEFI boot mode, after you resolve partition issues.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Testdisk may show old partition structure of your gpt partitioned drive.
      
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by adam121 on 2015-02-15
Thanks. 
Small bios partition is left untouched.
Grub was installed into /dev/sda first disk boot sector and efi boot partition was there when installing.
 Added boot flag only didn't formatted.

Will try to fix this now
Need windows basically for changing keyboard backlight in my alienware. 
Pyalienfx is not supporting my M17R5

Thanks

---

