---
title: "Trying to get Ubuntu to boot on the HP 110-210 desktop"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by Anthony_Mendoza on 2014-08-05
Has anyone managed to boot Ubuntu on the HP 110-210 desktop?  
 

 I haven't had much luck.  And there doesn't seem to be any real answers on the web that I have found.  I hope to find some help or at least someone else who is suffering through the same thing for some moral support.

 

 First what I have done:
 

 1) Installed Ubuntu with the simpliest configuration possible: /dev/sba1 for the boot partition, /dev/sba2 for the /root partition and /dev/sba3 for the swap partition.
 

 2) Tried to boot and I got that PXE message: Start PXE over IPv4 and it hung
 

 3) Disabled Secure Boot
 

 4) Disabled Legacy and Fast Boot in the BIOS
 

 5) Disabled PXE
 

 6) Ran the disk diagnostics and they passed
 

 7) Rebooted and got the following message: Boot Device Not Found.
 

 8) Booted with a live USB and then ran Boot-Repair.  Here is the log: [http://paste.ubuntu.com/7946771](http://paste.ubuntu.com/7946771)
 

 9) Rebooted without USB and got the same message: Boot Device Not Found
 

 10) Boot a live USB and then mounted the hard disk and looked around.  It appears that GRUB2.02 and the .efi file are on the hard disk.
 

(I also sent the above message to the HP support forum -- I am not too hopeful there, but who knows).

It seems to me that the HP BIOS is not finding GRUB for some reason.  Does anyone know where it looks?  Is it possible to reconfigure the HP boot so it looks in the right place?  Or does anyone have any other ideas or experiences?

Thanks,

Anthony

---

### Post by oldos2er on 2014-08-05
Moved to Installation & Upgrades.

---

### Post by Anthony_Mendoza on 2014-08-08
I'm back at trying to get the HP 110-210 desktop to boot.  I deleted everything off the hard drive using sudo rm -r /* (always wanted to that) and then reinstalled Ubuntu (still doesn't boot) and then ran boot repair again.  it failed again  ([http://paste.ubuntu.com/7985519](http://paste.ubuntu.com/7985519) for the curious).  I also reran the extended disk diagnostics and memory diagnostics too.  They all passed.

This is about as virgin a system as one can get.  I eliminated any possible complication.  There are minimum partitions and no other operating system.  There just seems to be something about this HP machine that Ubuntu doesn't like (or maybe HP doesn't like Ubuntu!).

Anthony

---

### Post by Anthony_Mendoza on 2014-08-08
I also did the following from a live session:

ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD
ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode" 
Installed in EFI mode
ubuntu@ubuntu:~$

---

### Post by Anthony_Mendoza on 2014-08-08
Hmmm.  There seems to be a disconnect between the BIOS below and GRUB above.  That is the EFI.  As you all saw in my last post, Ubuntu and the Hard drive are set to EFI mode.  Does anyone know where the EFI looks for GRUB?

---

