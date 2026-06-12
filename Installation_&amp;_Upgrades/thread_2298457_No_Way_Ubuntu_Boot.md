---
title: "No Way Ubuntu Boot"
date: 2015-10-11
forum: Installation &amp; Upgrades
---

### Post by essentiel on 2015-10-11
I'm using Lenovo Y50-70 with Windows 10 OS , I need to install ubuntu on my laptop but with Windows so I need dual boot system. I downloaded recomended version of ubuntu 14.02 , I crated bootable usb with recomended programme it went perfect. And than I restart my laptop I manipulate BIOS values such as I turned off secure boot, I tried both way UEFI and Legacy mode. In UEFI mode BIOS can not see my usb so my laptop start with Windows.I remove tick on the fast boot in control panel-power options in Windows and it didn't change.When I selected Legacy Mode I can see my Usb and I chose it and then I have PXE error so I turned off PXE Lan boot disable , and than again laptop start boot I can see option screen of ubuntu says me Try Ubuntu Without Install , Install Ubuntu etc. I choose Install Ubuntu and I got error like No bootable device , please insert or press any key.Finally I couldn't manage to install Ubuntu , I installed Ubuntu my desktop a year ago errorless and it going well. What can I do now?

I read a lot of topic in this forum but I couldn't do it. Please help me.Thank you.

---

### Post by oldfred on 2015-10-11
You may need to turn off secure boot and/or turn on allow booting from flash device or other devices. Often with UEFI & secure boot, they restrict what can be booted. Also turn off fast boot which is different than Windows fast start up, if you have that setting. With it on, you can have issues getting back into UEFI.

If Windows is installed in UEFI boot mode, which it will be if from vendor, you will want Ubuntu in UEFI boot mode. Best to use Windows to shrink its NTFS partition to make unallocated space for Ubuntu. And reboot into Windows immediately and make sure fast start up is off.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

When you boot is it using the Intel video or nVidia. Can you set that in UEFI or is it only automatic?
If Intel it needs a different setting than nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


Some other Lenovo

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

---

