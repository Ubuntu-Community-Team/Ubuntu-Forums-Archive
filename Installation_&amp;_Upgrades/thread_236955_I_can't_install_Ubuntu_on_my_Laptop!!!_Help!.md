---
title: "I can't install Ubuntu on my Laptop!!! Help!"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by LeMeun on 2006-08-15
Hello Everyone,

I try everything i can to install Ubuntu on my laptop:
MSI Megabook S271

Processor: Turion 64 bit Taylor Processor, dual core from AMD
- Sampron 64 bit, single core
- FSB 800 MHz

Chipset: ATI ® RS485M + ATI® SB460

Graphics & Video Module:  UMA ATI RS485M , VRAM 128

System Memory: DDR2 400 / 533 / 667 SO-DIMM x 2 slots, Max: 2GB (1024MB DDR2 SO-DIMM x 2) (1 GB DDR2 533from PQI 

presently installed)

Complet spectre here: [http://www.ubuntuforums.org/newthread.php?do=newthread&f=140](http://www.ubuntuforums.org/newthread.php?do=newthread&f=140)

I start with the live-cd version ubuntu-6.06.1-desktop-i386.iso to give a try and discover Ubuntu without getting dirty yet w the 64 bit version.





i press enter after the splash screen from Ubuntu (30s count down)
- loading /casper/vmlinuz.......................
- loading /casper/initrd.gz.....................

loader screen appear -> loading Linux kernel 100%

go to black screen

.
decompressing Linux... done.
booting the kernel.



and everything stop no further lines.

I try many of the boot options and nothing works, so maybe the i386 live-cd is not running on 64 bit duo core i though. 

Than i try the live-cd version ubuntu-6.06.1-desktop-amd64.iso, and the same thing happens
"booting the kernel" than nothing everything stop.

So i check my iso files with the md5 checksum -> ok
Check cd defect -> won't run stop at "booting the kernel"
I decide to test the i386 live-cd version on my P4 desktop and it work fine without any trouble. I saw Ubuntu and start to fall in love!

So i went back on my laptop decided to make it work.

I follow the advise from Usernamed and try to disable the framebuffer device:

boot prompt: live debian-installer/framebuffer=false -> didn't work!

I try both version of the alternate (i386 & AMD64) as Kilz advise me and still the same problem.

I never pass the stage of "booting the kernel", than nothing

I try everything those pass 3 days and i'm really hopeless:sad: , i think my laptop will never see Ubuntu.:confused: 

If anyone have an idea or an advise it'll be most welcome, thanks in advance for ur time and interest.

LeMeun

---

### Post by John.Michael.Kane on 2006-08-15
LeMeun can you please try the [**ubuntu-6.06.1-alternate install CD**]("http://ftp.iasi.roedu.net/mirrors/ubuntulinux.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso").the live cd seems to have some issues with some folks hardware.

---

### Post by LeMeun on 2006-08-16
I tryed the alternate version as well and i got the same problem.

But i find an issue about the Thinkpad T23 boot problem, the advice was to disable the acpi. And it works! I'm still amaze!\\:D/ 

After the splash screen of Ubuntu, push F6 
Here is my boot option:

casper initrd=/casper/initrd.gz ramdisk_size=1048576 **acpi=off** root=/dev/ram rw quiet splash --

I hope i didn't make mistake, please correct me if i do. Thanks
This work fine with the live-cd i386, i'll install the alternate this afternoon i let u known.

---

### Post by casperlingus on 2006-08-17
FYI:  I had a boot problem with Dapper and my Thinkpad T20.  It would boot to right before the login screen then freeze.  I was able to solve the problem by booting into recovery mode and changing the default color depth to 8-bits or 24-bits.  The 16-bits default display apparently doesn't sit well with older thinkpads.

Boot into recovery mode and either modify /etc/X11/xorg.conf (if you know how) or run ```
sudo dpkg-reconfigure xserver-xorg
```

I am running Ubuntu from the Alternate CD installation quite happily now.

Casper...

---

### Post by carontis on 2006-08-17
Well, there also the specific distro for 64 bit processors, why don't you use that one? (may be better the alternate 64 bit)

---

### Post by coleguinha on 2006-09-01
Hi...

I also have a MegaBook s271 :)

I had the same problem with ACPI and so on...

To solve this problem I would suggest you 2 options:

1. Just add the following lines in the end of the kernel boot line in the menu.lst of your grub installation:

... nohpet nmi_watchdog=0 noapic nolapic

Reboot and you'll have ACPI working :)

The problem is that the system sometimes freeze, the keyboard sometimes don't  work.. and so on...

2. Compile a new kernel for your laptop. The last stable version from kernel.org is 2.6.17.11

You can download it and copy the configuration of your current kernel (to save some time). Then you just search for the ACPI settings in the MENUCONFIG and enable them.

After compiling, install it and reboot. PLEASE DONT UNINSTALL THE OLD KERNEL.. just in case :)

You will still need the "nohpet" option in the kernel line, but it will run smoothly... very stable!!!!

NOTE: the network cards wont work because the vanilla kernel doenst support them. You'll have to search for the drivers and compile them for your new kernel.

The drivers are: r1000 (for the realtek 8168 ) and rt2500 (for the wireless card RaLink RT2500)


I hope this helps you!!!!

Cheers

---

