---
title: "After formatting a dual boot pc to a single boot one, grub does not appear"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by duygu2 on 2015-10-03
Hello to you all,

I was using both Windows 7 and Ubuntu 14.04 (Which was set as an update from Precise Pangolin) on my Lenovo Z570 PC. Since my windows became broken after 2 years, I formatted the PC to have only Thrusty Tahr (14.04). I have tried many options from the USB installer but none of them were effective to boot successfully. I have also tried Boot Repair. It did not work either. The summary files before and after BOOT Repair can be found below. Any help would be appreciated, thank you.

Before boot repair: [http://paste.ubuntu.com/12647336/](http://paste.ubuntu.com/12647336/)

After boot repair: [http://paste.ubuntu.com/12647381/](http://paste.ubuntu.com/12647381/)

---

### Post by oldfred on 2015-10-03
Some systems only want to boot a Windows entry as the also use description in UEFI. That is not per UEFI standard.

Back up entire efi partition before making changes:

 If that is the case, you can use a couple of work arounds. I might do both. You can make the fallback or hard drive boot be really grub. It probably is a copy of Windows efi boot file. Copy /EFI/ubuntu to /EFI/boot and rename shimx64.efi to bootx64.efi.

      
 Use efibootmgr if only Ubuntu, not dual boot, install to make Windows UEFI description boot grub or shim file
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
    
Details in link in my signature.

T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by duygu2 on 2015-10-04
Thank you very much for the detailed help. I will try to do the steps for only Ubuntu OS and inform you about the progress. Now I wonder whether there would be any problems if I want to make the PC dual boot again.

---

