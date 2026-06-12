---
title: "Cannot boot single boot on Toshiba Sat. C55"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by gary67 on 2015-09-30
Here is my Boot Repair info...... [http://paste.ubuntu.com/12627274/](http://paste.ubuntu.com/12627274/)
Error message upon boot is "Reboot and select proper Boot device...bla bla"

I can boot fine USB, or CD Drive

Any help is greatly appreciated, as I talked this guy into trashing his once again hijacked Windows...and now I can't get his laptop to boot....yeah...awesome.

---

### Post by ubfan1 on 2015-09-30
Your boot order should have the ubuntu entry first, but the ubuntu entry itself looks odd.  Mine looks like:
BootOrder: 0000,0004,0003,2003,2001,2002
Boot0000* ubuntu    HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(\EFI\ubuntu\shimx64.efi)

For a secure boot (works for both enabled and disabled secure boot) (grubx64.efi instead of shim for secure boot disabled)
Maybe take boot-repair's suggestion to reinstall the grub-efi-amd64-signed package?
efibootmgr can be used to reorder the boot order, as well as creating a new (correct) entry if you want to do it yourself (never done this myself).

---

### Post by oldfred on 2015-10-01
Another fix is to copy /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi.
Many new systems seem to need this as vendor's are violating UEFI spec. They modify UEFI to use description for UEFI boot and check that only valid description is "Windows".

Since you do not have Windows you can also do this, it thinks it boots Windows description but boots with shim or secure boot version of grub:
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Above assumes defaults of ESP as sda1. 
See man efibootmgr or 
      
 [URL="http://linux.die.net/man/8/efibootmgr"]http://linux.die.net/man/8/efibootmgr
[/URL]
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

[URL="http://linux.die.net/man/8/efibootmgr"]
[/URL]

---

### Post by gary67 on 2015-10-01
You guys are awesome...thank you.
I reinstalled Grub and renamed the file..and I am up.
Whew...

---

