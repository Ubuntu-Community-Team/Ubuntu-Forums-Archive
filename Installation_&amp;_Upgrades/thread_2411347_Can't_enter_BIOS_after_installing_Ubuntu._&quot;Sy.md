---
title: "Can't enter BIOS after installing Ubuntu. &quot;System BootOrder not found. Initializing D"
date: 2019-01-29
forum: Installation &amp; Upgrades
---

### Post by millenito on 2019-01-29
I recently installed ubuntu on a MBR hard drive, read some tutorials before showed that i need to install the bootloader on an efi partition, since i dont have an efi partition i created a 100mb partition (/dev/sda7) so that i could install the bootloader on it.


Ever since that i couldn't enter the BIOS again (previously by pressing F2), pressing F2 would just show the "Please wait..." text below the manufacturer's logo but then it boot straight to ubuntu.


I've tried reinstalling and and purging grub multiple timesusing the boot repair tool [https://sourceforge.net/p/boot-repair](https://sourceforge.net/p/boot-repair).
but each time i run a repair the log says that it's successfull 
[http://paste.ubuntu.com/p/mzjMGtXzZZ/](http://paste.ubuntu.com/p/mzjMGtXzZZ/)
```
Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your BIOS boot on sda7/EFI/neon/shimx64.efi file!
```




but when i reboot and press F2, the screen says
```
System BootOrder not found. Initializing defaults
creating boot entry "Boot0027" with label "ubuntu"...
```
for a split second (couldn't get the last few words since it was so fast)
then after checking the bootInfo log again the log says that it found an error and a suggested repair
[http://paste.ubuntu.com/p/hp86cM7HWn/](http://paste.ubuntu.com/p/hp86cM7HWn/)
So the cycle just keeps repeating..:(


NOTE:
I've also already tried setting ```
 GRUB_CMDLINE_LINUX_DEFAULT 
``` line to > quiet splash reboot="bios" in my ```
/etc/default/grub
``` file, but still couldn't enter the BIOS :(




I just needed to enter BIOS so that i can enable intel VT-x and run a vm. Any suggestions or guides would be really helpful. Thank you :hattip:

---

### Post by oldfred on 2019-01-29
What brand/model system?

You have mixed BIOS type install with UEFI type install.
BIOS normally uses the now 35 year old MBR and UEFI uses gpt partitioning.
Windows only boots in UEFI boot mode from gpt, but Ubuntu will work from MBR, but only suggested for live installer which works for both UEFI & BIOS install.

Windows boots so slow that Microsoft required fast boot setting in UEFI. That setting assumes no system changes so UEFI/BIOS does not scan drive for configuration nor then write that configuration to drive for operating system use. Because that is so quick, you often do not have time to press any key when booting to get into UEFI or UEFI boot menu to choose what to boot.
You need to turn off fast boot. You may be able to have more time as full cold boot usually does the system check, so more time.  Fully shutdown system, and remove all power including battery if laptop. Hold power switch for 10 sec or so. Then boot and immediately press correct keys to get into UEFI.

If you want UEFI boot better to start over and it will install with gpt partitioning.
If you want to stay with your MBR configuration, you need to install the BIOS boot version of grub.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

