---
title: "Boot problem after install"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by lop2 on 2015-04-22
Hi everyone,
I have tried installing Ubuntu onto an old sony laptop. The install went fine. However, Ubuntu won't boot after restart, instead I get an "Operation system not found" msg on a black screen.  I have tried the boot-repair diagnosis. The output file is at paste.ubuntu.com/10866971.
Sorry if this is obvious. Any help is appreciated on what to do or check.

---

### Post by mörgæs on 2015-04-23
Hi, welcome to the fora.

Let's see some details. From a live boot please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by oldfred on 2015-04-23
Is this your pastebin?
[http://paste.ubuntu.com/10866971/](http://paste.ubuntu.com/10866971/)

That is UEFI  with LVM full drive install. So not very old system at all.

But Sony's have not been dual boot or Ubuntu boot friendly. They violate UEFI and check description of boot entries and only allow "Windows".

If only booting Ubuntu you can change entry to read Windows but boot grub or shim.
        If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"
If using grub you must have secure boot off.

You do not show shim or the secure boot versions of grub, nor signed kernels. So this may will not currently work. Just make sure secure boot if off. 
If you want secure boot, but must install all the signed copies first.

 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

