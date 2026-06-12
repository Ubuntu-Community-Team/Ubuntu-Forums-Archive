---
title: "disk won't start install process"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by tiamatschosen on 2013-01-28
I have a Toshiba c855d-s5307 laptop. I redid a windows 8 installation and left 25GB free space to install 12.10 x64. secure boot is turned off and when I boot from the DVD I get the proper install/boot live  options.  But when I pick either one the disk spins for about 5 minutes then the screen shuts off and nothing happens until i restart.  I've tried the USB live boot, but it will not start up either

---

### Post by tiamatschosen on 2013-01-28
i have all 4 ubuntu ISOs.  which one would be the best to try.  and the UUI wont let me install the x64 versions for USB boot.

---

### Post by prabhanjan on 2013-01-28
check for dvd disc errors
or reburn it with slower speed

---

### Post by voodoomurphy on 2013-01-28
> **tiamatschosen said:**
> I have a Toshiba c855d-s5307 laptop. I redid a windows 8 installation and left 25GB free space to install 12.10 x64. secure boot is turned off and when I boot from the DVD I get the proper install/boot live  options.  But when I pick either one the disk spins for about 5 minutes then the screen shuts off and nothing happens until i restart.  I've tried the USB live boot, but it will not start up either

I purchased a C855D this weekend and went through the exact same thing. Here's how I got 12.10 64 bit working:

1. Boot into the bios and disable SecureBoot

2. Then change from UFEI boot to CSM boo. Select Advanced -> System Configuration -> Boot Mode. Then you do this, it WILL WIPE THE HARD DRIVE. 

3. Boot to the Windows 8 CD/DVD and install Windows 8 as needed.

4. Boot into Windows 8 and install 12.10 from WUBI.

I spent hours working on this and it's the only way I could get Linux installed. I tried multiple DVDs, USB sticks, multiple partitioning of the Hard Drive and sacrificing a chicken. The only way I even found this out is because I got completely pissed after the 14th time the install failed and said "screw it" and installed Windows 8 from a DVD so I could return the unit. I had originally intended to only use Ubuntu on this machine so I had wiped and re-partitioned the Hard Drive. It literally took me 8 hours to figure this all out on my own.

---

### Post by oldfred on 2013-01-28
voodoomurphy converted from UEFI/gpt partitioning to BIOS/MBR. wubi only works with MBR(msdos) partitioning.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Some systems will only install in BIOS mode, but then Boot-Repair can convert to UEFI mode by uninstalling grub-pc and installing grub-efi.
       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot

---

### Post by tiamatschosen on 2013-01-28
this is waht i have tried so far and the results:
UEFI:
12.10X64 DVD = spins for 2 minutes the sits and does nothing for an hour until i restart
12.10X64 USB = will not boot
CSM:
install windows 7(first x86, then x64), put in ubuntu(all 4 versions on dvd AND USB) = windows not found(500gb freespace).
windows 8 will not install on CSM mode.

considering the fact that windows only takes 5-15 seconds to boot im assuming that i have a hybrid ssd/hdd.


i am looking at these 3 laptops models as possible replacements which one would be the best for a dualboot:

Samsung - 15.6" Laptop - 4GB Memory - 500GB Hard Drive - Black
Model: NP365E5C-S05US

HP - Pavilion 15.6" Laptop - 4GB Memory - 640GB Hard Drive - Sparkling Black
Model: g6-2278dx 

HP - Pavilion 15.6" Laptop - 4GB Memory - 640GB Hard Drive - Sparkling Black
Model: g6-2239dx

---

### Post by oldfred on 2013-01-28
Windows always hibernates to speed boot.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
But some systems have Intel SRT if using Ultrabook label.
       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


       
 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
[       ]("http://ubuntuforums.org/showthread.php?t=2093445")
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

