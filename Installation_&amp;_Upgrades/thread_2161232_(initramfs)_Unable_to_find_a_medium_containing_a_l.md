---
title: "(initramfs) Unable to find a medium containing a live file system"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by jcooksey on 2013-07-09
When I boot from my USB stick for a fresh install, the following happens:
1.  Purple screen
2.  Ubuntu logo blinky dots
3.  Dropped to busybox shell, prompt reads "(initramfs) Unable to find a medium containing a live file system"

My system details:
Iso: ubuntu-13.04-desktop-amd64.iso
CPU: AMD FX-8350
MOBO: Gigabyte 970A-UD3
Note:  This is a new build.

Things I've done so far:
1.  Confirmed the md5sum on my iso.  I wrote the iso to my memory stick using usb-creator-gtk on my eeepc that runs ubuntu.
2.  Confirmed that I am not plugging the USB stick into a USB3 port.  I also disabled USB3 in my BIOS to be sure.
3.  Tried different USB ports.
4.  Changed SATA type to ACHI from IDE in my BIOS settings.
5.  Installed win7 successfully (from DVD), and verified USB port functionality with the stick I'm using to boot.  Installed FreeBSD successfully (from USB).  
6.  Failed to install the latest Debian and Arch distros (from USB).  The Debian and Arch installations both failed with the same error.  Something about unable to map USB ports.

So evidence is suggesting I have a Linux compatibility issue.  Does anyone have some suggestions?  I haven't had this much trouble installing Linux since like 1999, so it's a bummer.

Thanks.

---

### Post by fantab on 2013-07-10
BURN the ubuntu.iso using a different burning software, for instance try, [Unetbootin]("http://unetbootin.sourceforge.net/") or [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/") (Win32DI shows the extension as .img, you have to manually change the extension to .iso, if necessary).
Try DVD if USB is causing problems.

It will also be a good idea if you update your MoBo BIOS/UEFI firmware to the latest version. 

How did you install your Windows, in legacy BIOS mode or UEFI?

---

### Post by jcooksey on 2013-07-10
Install works with ubuntu-13.04-desktop-i386.iso.

Install still is not working with ubuntu-13.04-desktop-amd64.iso.

I haven't changed any BIOS system settings.  I'm using the same USB stick.  I wrote each iso using the same software.

---

### Post by fantab on 2013-07-10
What is your Graphic Card?

Does 64bit Ubuntu boot? I mean can you "Try Ubuntu Without Insalling"? Can you Boot Windows 64bit?

Check your BIOS/UEFI see what boot mode is enabled, UEFI or Legacy? If you are seeing purple screen during boot then your Ubuntu in not booting in UEFI mode. If it does then you will see a Black Screen with options.

Confirm your CPU is actually reporting itself as 64bit in the BIOS. (It is possible that you have a bad piece of Processor).

How did you partition your HDD? If you want to install Ubuntu in UEFI (recommended) then you will need to format the HDD Partition Table to GUID, aka, GPT. GPT is a requirement to boot in UEFI. You will also need to create your first partition as an EFI partition of about 300mb and format it with FAT32.

If you have a DVD drive then try to burn a DVD with .iso Ubuntu image.

---

### Post by jcooksey on 2013-07-10
> What is your Graphic Card?
Radeon HD 7770 2gig

> Does 64bit Ubuntu boot? I mean can you "Try Ubuntu Without Insalling"? 
No, I get the same error message as when I attempt to install.  

> Can you Boot Windows 64bit?
Yes, I installed 64-bit win7.  USB devices worked fine there.

> Check your BIOS/UEFI see what boot mode is enabled, UEFI or Legacy? If you are seeing purple screen during boot then your Ubuntu in not booting in UEFI mode. If it does then you will see a Black Screen with options.
When I select the boot device, it allows me to choose legacy (purple screen) and UEFI (black screen).  Both end up giving the same error when I attempt to boot.  This is using the amd64 iso.

> Confirm your CPU is actually reporting itself as 64bit in the BIOS. (It is possible that you have a bad piece of Processor).
Confirmed.  BIOS reports an 64bit 8-core AMD FX-8350

> How did you partition your HDD? If you want to install Ubuntu in UEFI (recommended) then you will need to format the HDD Partition Table to GUID, aka, GPT. GPT is a requirement to boot in UEFI. You will also need to create your first partition as an EFI partition of about 300mb and format it with FAT32.
I attempted the amd64 Ubuntu install first, when the drive was unformatted.  The installer never launched though.  When I installed win7, I used the entire drive.  When I installed i386 Ubuntu, I used the entire drive.  

> If you have a DVD drive then try to burn a DVD with .iso Ubuntu image.
I might try that, but I suspect USB devices would still be broken if the install succeeds.  It may be fixable after getting a clean install though.

---

### Post by Paul_Nagele on 2013-09-19
Has anybody found a solution for this problem?
I have got the exact same issue with the same hardware and Ubuntu version.

---

