---
title: "Ubuntu 13.04 works on one...not the other..."
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by gtrstitch on 2013-12-03
Okay, so, I will just get right into it.

I've successfully loaded Ubuntu on my wife's Toshiba Satellite (Live Mode) and everything worked fine. Networking was okay, etc. It was beautiful. I go to load and install on mine (which is the exact same model laptop) and after the Ubuntu load screen, it goes to what I can only describe as a display malfunction. Sometimes it's speckled white and blue bars, sometimes just what looks like a starfield. The two laptops are identical in every way except the HDDs. My wife's laptop is stock from top to botton, whereas mine had a major mechanical failure in the hard drive thus I had to replace it. Granted, it is a smaller and slightly older hard drive (2011ish, and only 160Gb) I did have Ubuntu 12.04 installed on it, running inside a restored and modified desktop. Ill mention that I did wipe and format the drive before restoring my Windows 8 OS onto it.

At any rate, I'd like to ask what could be the problem? Is it possible that the hard drive is causing some kind of failure upon loading? I've checked the BIOS settings on both laptops to ensure they match. SecureBoot is disabled. I be so confused. I would <3 running Ubuntu alongside my W8 OS, and maybe replace W8 over time.

I've got a few more troubleshooting options to try, but I would greatly appreciate some feedback and suggestions before venturing.

Thanks in advance!

~GtrStitch

EDIT - 13.10, not 13.04 :S

---

### Post by sudodus on 2013-12-03
Welcome to the Ubuntu Forums :-)

Could it be that the two computers have different hardware, for example some different type or version of graphics chip/card or wifi chip/card?

I don't think we should blame it on the HDD, particularly not if you have those problems in your computer also when you boot it live from the CD/DVD/USB drive.

You might be able get better results with some boot option, start to try ***nomodeset***. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gtrstitch on 2013-12-04
I had hopes that nomodeset would work...nada...Im so lost. Fastboot is disabled. Secureboot is also disabled. It almost seems like the live usb stick is stuck in a boot loop. Besides boot options, is there anything else that comes to mind for this type of situation? As for both the laptops, they are identical save for the hard drive. Software versions match across the board (verifying that was dizzying). I've used linuxlive usb creator, universal usb creator, and unetbootin. I am seriously confused on this one...

~GtrStitch

---

### Post by gtrstitch on 2013-12-04
Changed from UEFI to CSM (in ahci and compatibility) and it throws this error -
Authentication Failure
[   17.443309] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 14

---

### Post by oldfred on 2013-12-04
Post this just to see current partitions.

 sudo parted /dev/sda unit s print

Are/were both systems UEFI?

---

### Post by gtrstitch on 2013-12-05
I cant sudo since live or persistent mode wont boot. And if 13.10 is uefi, then yes, both systems are uefi.

---

### Post by oldfred on 2013-12-05
The installer 13.10 is both UEFI and BIOS depending on how you select it from UEFI menu. 
If not a new computer with UEFI then it is only BIOS bootable.


What video does system have? 
What model is it? As then we can look up specs to know details.

This shows both the UEFI grub menu and the purple BIOS boot screen that you may get.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you added nomodeset?
If grub menu you add it manually with e for edit and replace quiet splash with nomodeset.
If BIOS you hit any key at accessiblity icons, then f6 choose nomodeset.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gtrstitch on 2013-12-06
My graphics is AMD Radeon HD 7520G running on a Windows 8 (Toshiba Satellite C855D-S5351). My wife has the exact same model laptop which is able to run 13.10, whereas mine will not. Both laptops are up to date with software and drivers (versions match across both). I just have no idea why mind will not boot 13.10 (or any other version) but my wifes will. Could there be a problem with the BIOS?

---

### Post by oldfred on 2013-12-06
Do you have the same version UEFI/BIOS from Vendor?

Is your wife's system booting with UEFI or BIOS?

Some other Toshiba's and what they did.
 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

 How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by gtrstitch on 2013-12-07
Those don't really apply to me, I think. I attempted to boot my LiveUSB again, and the screen goes to my normal Win8 screen, but it's all garbled and non responsive. It's like it's trying to boot windows.

---

### Post by ubfan1 on 2013-12-08
Double check the BIOS firmware revisions -- Toshiba's originally had a problem with the key databases in Jan 2013.  My Toshiba S855 needed 6.60 or later for the firmware version to work.

---

### Post by gtrstitch on 2013-12-09
The most current version of the UEFI firmware is 6.2. I double checked on Toshiba's site and that is indeed the most up to date for my model laptop. Could it have something to do with the EFI boot for windows? Would it be possible to copy the EFI boot files from my wifes computer over to mine?

---

### Post by ubfan1 on 2013-12-09
You can check that the files in the EFI parititions on the two machines at least have the same sizes.  The signed/unsigned versions of grub will be different in size, and not sure what happens when you try to boot a signed grub with secure boot off.  Also check the files in /EFI/Boot.  There should be a bootx64.efi at least.  Since some boot attempts result i silent failures (like when the efi menu for a grubx64.efi is selected with secure boot enabled), the first fallback is to the /EFI/Boot/bootx64.efi.  I leave a copy of shim.efi there (since I use secure boot), but you could put a copy of grubx64.efi (unsigned) there or if you want to default back to windows, put a copy of /EFI/Microsoft/Boot/bootmfgw.efi.

---

### Post by gtrstitch on 2013-12-09
everything checks out. bootx64.efi and grubx64.efi are on the thumb drive. although where could i obtain shim.efi?the only file i see with shim is a .deb file named "shim-signed_1.3+0.4-0ubuntu3_amd64".

---

