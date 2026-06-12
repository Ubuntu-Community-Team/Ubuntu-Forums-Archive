---
title: "Sony Vaio Utrabook SVT13126CXS Works"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by stevejluke on 2012-12-20
Hi all, I just wanted to share how I got my Sony Vaio ultrabook up and running on Ubuntu 12.10.  There isn't anything new here, but I wanted to put it all in one place so people can see it works and all the steps needed to get it done.  I think some of the issues are not specific to this laptop.

**Product:** Sony Vaio SVT13126CXS ultrabook
**Hardware:** Touchscreen, multi-touch enabled clickpad/trackpad, webcam, stereo sound, SSD hard disk, platter hard disk.
**Starter OS:** Windows 8
**Boot type:** UEFI
**Complications:** Intel SRT, which uses a RAID configuration and the SSD to get the OS and applications to launch faster.

Here is what I did to get things to work:

**In Windows**

* Turn off Hibernation
* Turn off the Page File
* Use the Intel SRT manager to disable acceleration and clear the SSD drive
(Thanks OldFred: [http://ubuntuforums.org/showthread.php?t=20957](http://ubuntuforums.org/showthread.php?t=20957).  This made it possible!)
* Defragment the system disk (platter drive)
* Used the windows disk manager to shrink the C:\ partition to 100GB
* Downloaded Ubuntu 12.10 64 bit.
* Installed the LiLi ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)) and used it to generate a USB to install Ubuntu from.

Note: Not all USB flash drives work on this setup.  The first one I tried 9had worked on other computers) would not stay active during the boot-to-usb, so the installation would always fail.  A Staples Relay USB drive worked well.  Also, it seemed to work better when plugged into the USB closest to the front (farthest from the screen).  The other port would occasionally lose power.

**Configure the BIOS**

* Shut down Windows.
* Press the Assist button to launch the UEFI boot control menu
* Press F2 to start the BIOS
* Turn Secure Boot off
* Turn the UEFI/BIOS mode to Legacy (instead of UEFI).
--- Technically not necessary, but the boot-to-usb worked best 
--- when in Legacy boot mode
--- When in Legacy mode, you can't boot to Windows 8.  When we 
--- are done you will be able to turn it back on
* Change the Boot order so the USB comes before the hard disks. 
* Plug the USB drive in
* Press F10 to save changes and exit.

From there it was a pretty standard Ubuntu installation.  I am happy to report:

1- Full touchscreen support
2- The camera works (not fully tested)
3- Touchpad/clickpad works, clicks, with 2-finger scrolling
4- Stereo Sound works
5- Same screen resolutions as available in Windows 8
6- Bluetooth works
7- WiFi works
8- Batter charge meter works
9- Most FN key combinations work

What does not work:
1- FN+F1 is supposed to toggle clickpad on/off but it doesn't work
2- Brightness settings.

---

### Post by catbb67 on 2013-01-17
Hi,

Thanks for the post. Just want to clarify. Once you isntalled Ubuntu, are you still booting using BIOS legacy mode? Are dual-booting now?

---

