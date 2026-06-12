---
title: "dual boot issue with Lenovo y50 running windows 8.1"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by lfpineros on 2015-02-17
if this have been solved, please lead me to the right place.

but I've been trying to do a dual boot with windows 8.1 with Ubuntu 14.04. I have a Lenovo y50 that has a hybrid HDD. at first it wasn't detecting windows when it was installing from USB, so i saw people being recommended this guide:

[http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-81-And-Ubuntu-Dual-Boot-Guide.htm#step-heading](http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-81-And-Ubuntu-Dual-Boot-Guide.htm#step-heading)

pretty much through that guide ive:

-Backed up windows
-shrinked the windows partition
-turned off fast start up
-disabled secure boot

and still after running the installer, it wont detect an operating system. I've searched many places, some say its an issue with the Hybrid HDD, others say its a Lenovo thing. What ever it is, i would appreciate it if anyone can help me out. 

Thanks

---

### Post by oldfred on 2015-02-18
With the newer Ubuntu many say you just need to change from RAID or Intel SRT to AHCI and then you can install.
Before the Intel SRT used RAID and we had to remove the RAID meta-data on drives, so Ubuntu desktop installer would work. 
Do you also have dual video? That also can cause issues.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

Do not know if any of these are similar to your model. Often vendor issues are common across models.

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

---

### Post by oldfred on 2015-02-18
Another y50 thread on nVidia driver install issues.
[http://ubuntuforums.org/showthread.php?t=2265315](http://ubuntuforums.org/showthread.php?t=2265315)

---

