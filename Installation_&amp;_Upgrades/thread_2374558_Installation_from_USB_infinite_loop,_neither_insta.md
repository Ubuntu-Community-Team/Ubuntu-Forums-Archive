---
title: "Installation from USB: infinite loop, neither install nor try without installing work"
date: 2017-10-17
forum: Installation &amp; Upgrades
---

### Post by somerandomfinn on 2017-10-17
Hello,

I am new to Linux. I had installed a different distro (not Ubuntu) on a desktop, but left it lying unused for a few years. (Getting going with Linux can be a bit intimidating...^^) Now I decided to give it another go, and switch to Ubuntu. But I can't get it to install. I don&#8217;t know what information is relevant, so I&#8217;m including a fair bit. Let me know if you need more.

Motherboard: fm2-a75ia-e53, MS-7792 ver: 1.1
No additional graphics card (except whatever is on the motherboard)
RAM: 2 x &#8220;Ripjaws X / G.skill&#8221; F3-17000CL11D-8GBXL
Harddrive: Samsung SSD 840 PRO
Version/ISO: Ubuntu 16.04.3-desktop-amd64
I flashed the ISO on a USB (ScanDisk) on a Mac using &#8220;Etcher&#8221;

What happens:
When powering up the computer I get a notification of auto detect analog input, then a motherboard (msi) screen. And then a screen with a picture of a keyboard and a person, presumably the visual version of &#8220;press any key&#8221;.

1) Not pressing anything
If I don&#8217;t press any key, within a few seconds the screen goes dark and I never get the prompt again. And pressing any key at that point does nothing.

2) Pressing a key (enter)
If I press enter I get to a language select screen, with 6 other options at the bottom (F1 help through F6 other options). Selecting English and continue (enter) takes me to the options of trying without installing, installing, etc.

- Choosing either &#8220;Try Ubuntu without installing&#8221; or &#8220;Install Ubuntu&#8221; have pretty much identical results: I get some notifications: Auto Detect (Analog Input), Entering Power Save; Auto Detect (Analog Input); then the msi logo & tagline. After that it takes me back to the initial screen with a person and a keyboard.

Sometimes (rarely) it recognises that I press a key. Then I am taken back to the same options (try without installing, install, etc.). Often (usually) it doesn&#8217;t recognize my frantic key pressing. In which case, after  a few seconds of the &#8220;press any key&#8221; -screen the monitor goes dark and nothing happens for a while.

After sometimes a short while, sometimes a number of minutes, I will get notifications about the monitor (&#8220;auto detect analog input) and again be shown the motherboard msi screen. And then be back to black.

I have tried reinstalling the ISO on the USB a number of times. Same result.

Can anyone link to any troubleshooting ideas I can try, please? Many thanks for any help!

(Edited to add some information)

---

### Post by slickymaster on 2017-10-17
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by oldfred on 2017-10-17
That is an UEFI motherboard. But new UEFI has backwards compatiblity with BIOS, if you really want the 35 year old BIOS/MBR configuration on new hardware.

The person/keyboard icons are from a BIOS boot. From UEFI you should get two boot options for Ubuntu live installer. One is UEFI:flash and other just flash which is then the BIOS boot. Flash will be name or label of flash drive you are using.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
I have seen issues with using Mac to create PC bootable flash drives. You can try this UEFI only method.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040

      [/URL]
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040) 
   Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

