---
title: "Live CD hangs on black screen"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by temporalburst on 2013-04-03
I'm trying to dual boot Ubuntu 12.10 with my current Windows 8 install, but the Live CD gives a black screen with a blinking underscore (no errors or anything, just blank) when I select "Try Ubuntu." I've disabled Fast Boot in my BIOS, Secure Boot is off, and I've tried all of the F6 options, and still nothing has worked. I've also tried both UEFI and legacy booting the Live CD. I have no idea why it's not working.

-Build Info
Intel Core i5-3570K 3.4GHz
Asus P8Z77-V PRO
Samsung 8GB (2 x 4GB) DDR3-1600
Western Digital Caviar Blue 1TB 3.5" 7200RPM HDD
Crucial M4 128GB 2.5" SSD
Gigabyte Radeon HD 7970 3GB
Asus DVDE818A7T/BLK/B/GEN

Note: I've only tried the 64-bit disk so far, and I'd like to avoid using the netboot installer if at all possible as my internet connection is quite slow.

---

### Post by oldfred on 2013-04-03
Did motherboard include secure boot? Most have not, yet.

Seems more like a video issue. Do you have Intel or your AMD video as boot choice. I think some disable internal or only use internal to boot to get system started.

I have nVidia, so not real familiar with AMD. 
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
sudo apt-get install fglrx
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by temporalburst on 2013-04-03
The motherboard includes secure boot, but it's disabled.
I'm not sure whether Intel or AMD is used for boot, I didn't see that as an option anywhere. But my graphics card is AMD. I don't even get into a live system though, I get a black screen before I reach that. Also, I've tried nomodeset and that doesn't seem to make a difference.

---

### Post by oldfred on 2013-04-03
Some of the new motherboards with i-series processors need other boot parameters also.

 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Not sure if a different brand might need similar settings?

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset


 dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems Asus
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

### Post by temporalburst on 2013-04-03
Setting acpi=off and nomodeset on the F6 menu actually brought up the Ubuntu loading screen with the four dots for once, which is as far as I've gotten, but restarting and doing it again didn't reach the loading screen. The boot options didn't work either.

---

### Post by temporalburst on 2013-04-03
I updated my BIOS and tried again a few more times, and one of the times I got this error, with nothing else on the screen:

```
udevd[128]: timeout 'ata_id --export /dev/sr0'
```

Don't know if that is of any importance at all.

---

### Post by oldfred on 2013-04-03
Some with BIOS and maybe UEFI have had settings that cause issues. Like enabling a floppy drive in BIOS, but having no floppy. Or having a blank CD in drive but system cannot read it. 
Or maybe secure boot on and it cannot boot a DVD?

---

### Post by temporalburst on 2013-04-04
Okay, I managed to get it installed. It was the optical drive, I unplugged it and it installed just fine.

---

