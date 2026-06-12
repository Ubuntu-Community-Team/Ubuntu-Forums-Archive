---
title: "Problems with UEFI disabled."
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by caffeine_freak on 2013-10-15
I purchased a new PC and it has windows 8 installed.  I went into the BIOS and disabled UEFI.  I tried to boot a Ubuntu Desktop Disk and the PC wont allow it.   The DVD is not spinning.   I have set the BIOS to boot from DVD.    

Can i blow away the Win 8 install on the drive?  Will this make installing Ubuntu easier.  I dont need windows but I wanted to make sure that my PC will be fine running Ubuntu before blowing away M$.  I read that the OS is tied to the hardware so If i blow away windows will my PC still work?

I am looking for the easiest fasted way to get Ubuntu running.   I have read a lot about UEFI and am very confused about what parts of what I have ready apply to me and my set up.    The BIOS has the option of disabling UEFI so I cant understand why it will not boot.

---

### Post by oldfred on 2013-10-15
Often best to turn off secure boot but not turn off UEFI. Some laptops have limited settings and with secure boot off, it only has one boot option that is UEFI if UEFI found or BIOS if MBR found with boot loader.
If you have secure boot on, only those systems seen as secure boot will even be shown.
Also if you have not turned fast boot off in Windows or UEFI you need to do that also.

What system? And what video does it have?
Often video is also an issue, and if a Ultrabook, you may have issues with Intel SRT which uses RAID.

More info in link in my signature.

---

### Post by caffeine_freak on 2013-10-15
Gateway sx2370 UR12   AMD Quad Core A6-3620 APU  6GB DDR3 DVD Super Multi.
AMD Radeon Graphics

Quiet Boot is disabled I dont see a Fast Boot.  The BIOS is from ACER and the MOBO says ACER on it,  the MOBO is a DAA 75L aParker 1105-1

The Only place UEFI is listed in in Boot Options as the second boot device.  UEFI:  HL-DT-ST DVDRAM GH82N.

I dont see a place to disable UEFI.  I do see Secure Boot under the Authentication Tab of the BIOS and secure boot is now disabled.

---

### Post by oldfred on 2013-10-15
I do not know all the details on AMD, often nomodeset is required.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Next version of kernel has some changes for AMD cards.

 The AMD Radeon Performance Is Incredible On Linux 3.12
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)


 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by caffeine_freak on 2013-10-15
I tried the nomodeset at the end of the kernel boot line.  The DVD does not spin up after I hit enter.  Nothing happens.  I am wondering if there is still a problem with UEFI not allowing the DVD to boot or stopping the PC from proceeding with the boot process.

---

### Post by caffeine_freak on 2013-10-15
I have a sony external DVD I plugged into a USB port.  I can see it in the BIOS and have set it as the primary boot device.  The PC will not boot from that DVD.   If I hit F12 to see the boot menu I do not see the DVD device listed.  I only see the windows Boot manager.  I also do not see the internal DVD device that was on the F12 boot list prior to plugging in my external DVD.

---

### Post by caffeine_freak on 2013-10-15
Also of note when booting UBUNTU 13 from my external drive I see the old school boot list not the newer boot screen shown in the first link on your post above  I do not have the function keys available.  The only way for me to modify the boot parameters is by down arrow to the selection and pressing 'e' to append the kernel line.   I am wondering if this is a graphics issue as you are discussing.   My external DVD is now spinning but i see no ouput on the screen.

---

### Post by oldfred on 2013-10-15
You probably want to boot in UEFI mode and that gives you a grub menu that you have to manually edit. 

Only if you really want to install in legacy/BIOS/CSM mode do you boot DVD or flash drive in BIOS mode that gives purple screen.

Sometimes these force different video modes to get you into system so you can use it. If one works then you will probably need it on first boot or until you permanently install proprietary drivers.
On grub menu use e, scroll to linux line and replace quiet splash with one of these.
        xforcevesa
 or
 nouveau.modeset=0
or
radeon.modeset=0

---

### Post by caffeine_freak on 2013-10-15
I tried all 3 in your last post and also tried the NOMODESET.  I see the black screen and hear the external drive spin but no install commences.

---

### Post by caffeine_freak on 2013-10-15
I booted into the first boot screen and at the grub> prompt i ran videotest.   in the upper left corner there is a small red square next to that diagonally toward the lower right corner is a light blue square.  another dark blue square is in the middle of the screen.  The text :"the quick brown fox jumped over the lazy" is nested inside that square.   so colors and text are visible.  Not sure why.

---

### Post by oldfred on 2013-10-15
Is your grub> from your installer or after you have installed?

It sound like you may not have  a good download or good install.

You can confirm that download is good:
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by caffeine_freak on 2013-10-16
Grub is from the installer.   I am still wondering if this is a video compatibility issue.  That is why I ran that test.  I dont know what the results of the test mean.  I will try to install from USB.   

I ran the md5sum and they are fine.  My DVD burn seems fine.

---

### Post by oldfred on 2013-10-16
If you are getting grub from DVD or flash drive installer that is a UEFI boot. BIOS/CSM boots with new UEFI systems use syslinux.
But if new UEFI system you probably want UEFI boot. But you should get grub menu as shown below. A few older UEFI systems will only boot with BIOS mode. But they may have fixes in a new UEFI/BIOS from vendor.
Both screens shown here:
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by caffeine_freak on 2013-10-16
I have UEFI enabled.  I have secure boot disabled. 
I shrunk my disk with the windows utility compmgmt.msc

I am booting into the old style non gui black grub boot screen and editing the linux line.  I have added nomodeset and the other 3 options you suggested. 
I have tried to boot from my internal DVD, external DVD and USB live.

My Win !3 Install has a 400 MB Recovery Partition, 300 MB EFI System Partition, Win Partition, 450 GB soon to be Ubuntu partition and a 13 GB recover partition.
 No luck.

---

### Post by oldfred on 2013-10-16
Are you using the 64 bit version? It is the only one with UEFI capability.

---

### Post by caffeine_freak on 2013-10-17
Yes it is 64 bit.  I know the image will work.  When i created the USB stick i was able to boot into ubuntu with the Virtual Box tool that was installed on the stick by the tool linux live USB creator.

---

### Post by oldfred on 2013-10-17
I think some others with Gateways have had issues but I do not know about AMD systems with AMD graphics.
Is UEFI/BIOS most current version from Gateway?

---

### Post by caffeine_freak on 2013-10-17
I tried to find a location where i could obtain an updated BIOS.   I was not able to find anything on the Gateway website or elsewhere.  I opened the case and the MOBO is stamped with "Acer inc"  "DAA75L aParker 1105-1    The BIOS states that it is version P11-A3  12/20/12.    I would try the Acer site for a BIOS but the somewhere, I think on the boot screen the statement "only use a Gateway BIOS or warranty is voided" blah blah blah

---

### Post by caffeine_freak on 2013-10-17
I managed to stumble across the support website.  It seems there are quite a few BIOSs available and even dedicated linux BIOS. Very cool.

BIOS
Description	Vendor	Version	Size	Date	Download
BIOS	Gateway	      P11.A4	2.6 MB	06/11/2013	Download BIOS_Gateway_P11.A4_Windows.zip
BIOS - UEFI for Windows 8 (Not for Upgrades)	Gateway	P11.A3	2.8 MB	01/29/2013	Download BIOS_Gateway_P11.A3_Windows.zip
**BIOS for Linux - UEFI for Windows 8 (Not for Upgrades)**	Gateway	P11.A1L	2.8 MB	01/17/2013	Download BIOS_Gateway_P11.A1L_Linux.zip
BIOS - UEFI for Windows 8 (Not for Upgrades)	Gateway	P11.A1	2.6 MB	01/17/2013	Download BIOS_Gateway_P11.A1_Windows.zip
**BIOS for Linux**	Gateway	P01.A3L	1.5 MB	12/26/2011	Download BIOS_Gateway_P01.A3L_Linux.zip
BIOS	Gateway	P01.A3	5.8 MB	12/26/2011	Download BIOS_Gateway_P01.A3_Windows.zip

---

### Post by oldfred on 2013-10-17
There really should not be a different UEFI/BIOS for Linux. UEFI is a standard that both Windows & Linux should comply with and work without issue. 
It sounds like that Gateway has a Windows only UEFI with internal changes that do not comply with UEFI standards. That they have different versions may mean they did not provide enough nvram for full correct UEFI for both.

Some Samsungs had major issues and it turned out that if their UEFI nvram got over 50% full system became a brick. Linux had to create work around to make sure nvram was not too full. Had to do more with not clearing nvram memory when released. Originally blamed on Linux but found it would happen in Windows eventually.

---

### Post by caffeine_freak on 2013-10-18
I discovered that Gateway support was not useful or helpful.  I asked four times what the Linux BIOS was for and they simply avoided the question.  I tried to install it to see what would happen.   The error stated it needed to be installed with DOS and that is was a 32 bit BIOS.  Not sure why it was listed on the page for my specific model.   In any case I did perform the upgrade to the latest BIOS for my PC.  Still having the same issue with not being able to see anything after the GRUB non GUI screen.

---

### Post by oldfred on 2013-10-19
If you get grub menu then it may be a video issue. 
What video chip?
Have you tried recovery mode?

Often nomodeset works. Use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

But some systems need different settings depending on video chip.

---

### Post by caffeine_freak on 2013-10-24
Radeon HD 6530D  

I am not sure what you mean by recovery mode?

nomodeset did not work for me.

---

### Post by oldfred on 2013-10-24
Recovery mode is the second entry in the grub menu. It may be in a sub menu if you have a lot of entries.

---

