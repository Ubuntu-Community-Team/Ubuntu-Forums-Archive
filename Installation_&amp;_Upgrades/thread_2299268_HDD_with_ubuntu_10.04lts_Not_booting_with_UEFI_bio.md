---
title: "HDD with ubuntu 10.04lts Not booting with UEFI bios"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by John_Stergiou on 2015-10-17
Please help, i have an HDD with Ubuntu 10.04LTS with programs on it that are not compatible with more recent versions of ubuntu. My new PC has the ASUS   885PLUS mobo witch runs on UEFI bios. The thing is it cannot boot my HDD. Is there someway i can get it to boot. Please Help

---

### Post by sudodus on 2015-10-17
Welcome to the Ubuntu Forums :-)

Ubuntu 10.04 LTS has passed end of life and receives no support, not even security updates. You can use it, but you should avoid connecting it to the internet.

I think support for UEFI was introduced with Ubuntu 12.10 and ported to Ubuntu 12.04.2 LTS (the second point release). I think it will be hard to make 10.04 work with UEFI.

1. Maybe you can run it in a virtual machine.

What I suggest is to run a current version of Ubuntu in the new PC. Run a virtual machine, for example VirtualBox, in the current version of Ubuntu. And run Ubuntu 10.04 LTS in the virtual machine.

2. Maybe you can keep an old computer or get a middle-aged computer (second-hand), and run Ubuntu 10.04 LTS in such a machine. It is still easy to find computers, that run in BIOS mode or at least can switch between UEFI and {CSM alias BIOS} mode.

---

### Post by grahammechanical on 2015-10-17
What is the problem? The motherboard not detecting the old hard disk? Or the motherboard not loading Ubuntu 10.04 on the old hard disk?

Does this new machine have Windows 8 or Windows 10 pre-installed. Machines with those two versions of Windows will not only have a UEFI boot system but also Secure Boot and Ubuntu 10.04 cannot load with secure boot enabled. Newer versions of Ubuntu can load with secure boot enabled although some users have found that it is necessary to switch off secure boot anyway.

There is another problem with machines that have Windows 8 and Windows 10 pre-installed. Windows will be installed in EFI mode. And that means that Ubuntu will have to be installed also in EFI mode. And Ubuntu 10.04 will not have been installed in EFI but in BIOS mode. You may need to enter the UEFI boot system and change to BIOS/CSM/Compatibility mode in order to load Ubuntu 10.04 and then when you want to load Windows you go back into the UEFI boot system and select EFI mode to load Windows.

So, you see, a lot depends on the set up of that new machine.

Regards.

---

### Post by oldfred on 2015-10-17
If you just want to boot the old drive, does UEFI/BIOS see drive?
Then you have to turn off Secure boot & UEFI and turn on CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Then you can in BIOS mode see if you can boot the old drive.

---

