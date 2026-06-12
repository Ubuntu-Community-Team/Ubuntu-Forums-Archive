---
title: "Boot loader not working, Windows 8.1 boots automatically"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2014-12-18
I just installed Ubuntu 14.10 on a second smaller HD (250 Gb). The larger HD (1 Tb) is hosting Windows 8.1.
After a long time installing, I clicked to restart, however for a long time nothing happened. The screen had already gone black but the pc was still running. I must have waited about 10 minutes. So I forced it to go off by holding the start button down.
Then I started the pc. But no booting choice was offered. Windows booted right in.
Any ideas?
When installing Ubuntu I chose the sdb disk as the location for the boot file. Not sdb1, I read somewhere that if I did choose sdb1 (or 2, 3, 4) I'd have to manually add Ubuntu in the MBR file.
Am I supposed to manually add Ubuntu in the MBR file now anyway?

Thanks guys,

JDL

---

### Post by grahammechanical on 2014-12-18
I would like to make 2 points.

1) If Windows is installed in EFI mode, then Ubuntu must be installed in EFI mode.

2) If the Grub bootloader is installed on to sdb, which is a fine thing to do, then sdb must be the drive that the boot system is looking to and not the Windows 8 drive.

I have 2 hard disks and I can select in the boot system (BIOS, in my case) which hard disk to boot from. If your system is booting from the 1TB drive then it will load straight into Windows because even if you could re-configure the Windows boot loader it will not detect Ubuntu on the other hard disk.

Regards.

---

### Post by javierdl on 2014-12-18
Thanks for replying GM.
I think my motherboard is EPU, not EFI. AMD Phenom II X3 710, motherboard= [http://www.asus.com/Motherboards/M4A78E](http://www.asus.com/Motherboards/M4A78E) 
So what now? Reinstall Ubuntu so I can choose the 1Tb drive? I hope not

---

### Post by oldfred on 2014-12-18
If your system is BIOS, you should just be able to go into BIOS and choose to boot from sdb. Then it will find the grub you installed to the MBR of sdb. 

If that does not work then we need more details and this will show many details of your installs.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by javierdl on 2014-12-19
Thank you so much oldfred, indeed it was as simple as switching the HDs around in the BIOS ;)

JDL

---

