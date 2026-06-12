---
title: "Win 8.1 &amp; Xubuntu 16.04 dual boot issues"
date: 2016-07-11
forum: Installation &amp; Upgrades
---

### Post by ph3x on 2016-07-11
Greetings,

I´m playing around like several hours trying to get Win8 dual booting with Xubuntu 16.04

Laptop is always booting Win8, however if I start the boot menu (F9) I can also start Xubuntu.

boot-repair wasn´t able to fix the issue, even if I set the bootmgr like described.


[http://paste2.org/fkhzDILc](http://paste2.org/fkhzDILc) this is the link to my boot-repair log.

Please advice.

Cheers,
Christian

---

### Post by oldfred on 2016-07-11
You have 4 Windows UEFI boot entries in UEFI's NVRAM.
sudo efibootmgr -v

But one of those entries was an old work around to get Ubuntu to boot. It had you rename the Windows boot entry to really boot shim and then have grub boot the Windows bkp... backup bootx64.efi file.
But grub is booting the Windows efi file name which really just is shim/grub or an infinite loop.
A really old copy of Boot-Repair may have done that? Or did you do it? 
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 
 	[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

Delete 0003, 14 & 15. Some UEFI require all 4 hex chars, others just the last one or two significant digits.
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

What brand,model system?
Some modify UEFI to use Description as part of boot. That is not allowed per UEFI spec. And of course only Description that works is "Windows Boot Manager".
But all newer UEFI also allow fallback or hard drive boot entry to work. And you may be able to make that first in boot order.

Not now sure what your .efi files are.
Best to fully back up your ESP - efi system partition.
Is /EFI/Boot/bkpbootx64.efi a copy of Windows /EFI/Microsoft/Boot/bootmgfw.efi? You have to compare file sizes.
And you want bootx64.efi to be a copy of shimx64.efi.

---

