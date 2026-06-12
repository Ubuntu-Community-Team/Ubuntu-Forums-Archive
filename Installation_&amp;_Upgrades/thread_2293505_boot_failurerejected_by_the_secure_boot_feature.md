---
title: "boot failure:rejected by the secure boot feature"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by invis'222 on 2015-09-05
i am trying to install ubuntu 14.04.3 onto a toshiba satellite everything goes ok but when i restart i get a message saying "boot failure: a proper digital signal was not found one of the files on the selected boot device was rejected by the secure boot feature" i can run in "try ubuntu mode,
whilst in that mode i ran boot repair  and the message i got to write down was [http://paste.ubuntu.com/12282284/](http://paste.ubuntu.com/12282284/)
any help please

---

### Post by ajgreeny on 2015-09-05
Have you tried turning off secure boot in the UEFI setup?  That might be all that is needed.

---

### Post by oldfred on 2015-09-05
In addition to ajgreeny's suggestion.
Some vendors, not sure with Toshiba have modified UEFI to include UEFI description in boot. And only valid description is "Windows". That is not per UEFI standard.

Since you only have Ubuntu installed you can change the description for the UEFI entry. Instead of saying ubuntu we make it say "Windows", but actual file used is grub  or shim (for secure boot).

       Backup entire efi partition before making changes.


 
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Above assumes several default in entry, but should work. Details on efibootmgr entries:
       [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

