---
title: "Live USB Issue"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Chenorax on 2013-04-03
It's been a couple of days and every similar issue that I find on this topic does not have a working solution to my problem. For starters, I just want a dual boot system with Ubuntu and Windows 7. Once I boot from my USB and select Try Ubuntu it just comes to a black screen and the light on the USB stops blinking. What I just described was me booting in UEFI Mode or whatever. When I go into my BIOS and choose Legacy mode I can boot into the live USB fine. I've also tried editing the "splash quit"
things with "nosplash noquit", that didn't work (in UEFI mode). I also added nomodeset after noquit, but that didn't work either.
PC Specs: Intel Core i7 at 3.4GHz (8 cores, 4 virtual)
A Nvidia Geforce GTX 555 graphics card (1GB of onboard memory)
16GB of DDR3 memory
and I'm trying to install to a 256GB SSD
If you need more information feel free to ask, I didn't really know what to put

---

### Post by C.S.Cameron on 2013-04-03
What version of Ubuntu are you trying to install?
12.04.2 seemed to work ok for me.

---

### Post by Chenorax on 2013-04-04
I've tried 12.10 and 12.04.2, neither of them work with UEFI boot mode.

---

### Post by C.S.Cameron on 2013-04-04
Have you tried the drive in a different computer?

---

### Post by Chenorax on 2013-04-07
Yes, and it did boot normally.

---

### Post by oldfred on 2013-04-08
Is your Windows 7 in UEFI mode. It is difficult to dual boot unless both systems are either UEFI or both BIOS. You have to go into UEFI/BIOS and change modes to change which you boot.

You have nVidia and need nomodeset to boot. I have to use nomodeset on every install and first boot. With UEFI you use grub to boot, so you need to use e on grub menu and add nomodeset to linux line.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by Chenorax on 2013-04-08
Where on the Linux line do I put nomodeset? I had put it at the very end, pressed F10 and it still went to a black screen.

---

### Post by Bashing-om on 2013-04-08
Chenorax; Hi !

Look for a line similar to this:   linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff ---> see:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for complete disclosure.[INDENT=4]
hope this helps

[/INDENT]

---

