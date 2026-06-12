---
title: "UEFI error preventing me from installing ANY Linux distro"
date: 2018-08-07
forum: Installation &amp; Upgrades
---

### Post by eirinjas2 on 2018-08-07
I have a Toshiba Satellite C50D-A laptop that I want to install Linux on.  It came with Windows 8 installed, and has since been updated to Windows 8.1.  I have tried installing a number of distros, but all of them give me the "problem loading uefi db x.509 certificate (-65)" error, freezing the system.

Disabling Secure Boot doesn't help.  Disabling Secure Boot & choosing the legacy option instead of UEFI allows me to run a live CD/USB, but if I run the installer from within the live image environment it tells me there is no detectable operating system.  I assume this is because UEFI / GPT is not compatible with Legacy BIOS / MBR.

What can I do?

---

### Post by ubfan1 on 2018-08-07
mmartinsthiago, you should start you own thread, as your problem is unlikely to UEFI related, as this title indicates.  erinjas2, The first thing to do on a machine that old is to check for any firmware updates from the vendor.  The first Windows 8 machines had many problems as the vendors were unfamiliar with the secure boot issues -- most fixed by later firmware updates.
Next step, hashcheck the downloaded ISO you are using.

---

### Post by oldfred on 2018-08-07
Moved mmartingsthiago to his own thread.

Some similar Toshiba. UEFI update may help a lot.
Many Toshiba's will not boot Ubuntu by description. Only valid description is "Windows Boot Manager" and using description like that to limit boot is not allower per UEFI standard. 
So various work arounds then have to be used. Depending on configuration one or other may be better.
       Toshibs C55-B5356 "Failed to open \EFI\BOOT\grubx64.efi - Not Found" 
[https://ubuntuforums.org/showthread.php?t=2387851](https://ubuntuforums.org/showthread.php?t=2387851)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by eirinjas2 on 2018-08-07
Thanks for the reply.  I verified the hash on all the variants I downloaded.  I have the last version of the bios released for this particular model (ACPI FLASH BIOS VERSION 1.30 FOR SATELLITE C50D/C55D/C55Dt).  I noticed that other models in the C50 series have more recent bios updates in the same numerical pattern (1.40, 1.50, 1.60).

---

