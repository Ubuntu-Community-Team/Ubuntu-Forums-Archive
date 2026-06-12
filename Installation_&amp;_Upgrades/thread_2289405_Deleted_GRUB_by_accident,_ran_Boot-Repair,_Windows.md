---
title: "Deleted GRUB by accident, ran Boot-Repair, Windows OS still gone"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by russ18 on 2015-08-03
Hello,

I had this machine setup with an Ubuntu partition, a Windows 7 partition and another *nix partition. I deleted the Ubuntu partition so I could extend Windows' storage capacity as I wasn't using the Ubuntu anymore. Bad idea, clearly. 

I ran the Boot-Repair utility exactly as stated. Here is my Boot-Info URL.
[paste.ubuntu.com/11997000/]("http://paste.ubuntu.com/11997000/")

Any help interpreting what I might do differently to get GRUB to see Windows as a boot option would be very, very appreciated.

Thanks in advance,

Russ

---

### Post by oldfred on 2015-08-03
Both Windows & Ubuntu are BIOS based on MBR(msdos) partitioned drive.
But you booted Boot-Repair in UEFI boot mode. So you must have newer hardware.

But since your installs are BIOS, you need to make sure you have UEFI with secure boot off, UEFI off, and CSM/BIOS/Legacy or whatever your system calls it on. 
Best to also boot Boot-Repair in BIOS mode.

If you change UEFI to CSM boot in UEFI, then it should boot.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Have you run this when in Ubuntu?
sudo update-grub

        Grub only finds & boots working Windows.
Boot-repair report is not showing any major issues, but sometimes Windows needs chkdsk. Or if you left Windows hibernated then it will not work from grub.

---

