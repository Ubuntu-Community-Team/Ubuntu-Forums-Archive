---
title: "HP pavilion win 8.1. options for ubuntu"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by matt18 on 2015-03-03
Ello. I am in the midst of figuring out an option for my lap top. I only have 1 slot for a HDD and with the hp and win8.1 protection stuff, hp says it can be difficult to install another operating system alongside win 8.1 thanks to microsofts little drive protection. I see their reasoning but makes my life a lil more difficult. haha. I do have usb 3.0 and my internal HDD is 5400 rpm. Would it be a good idea to install to a usb 3.0 drive and boot from that? would it b able to run smoothly and fast or would it just be best to run it in vmplayer? 

It does run somewhat sow in vmplayer. I have dedicated 4gb ram from my 12 available. 

thanks

matt

---

### Post by grahammechanical on 2015-03-03
From what I have heard HP also modify the UEFI boot system so that it only loads the pre-installed Windows 8.1. There is a work around.

---

### Post by ubfan1 on 2015-03-03
I run off an 8G USB3 stick just fine, but I have moved things like /tmp and /var/log into a ramdisk.  The grub-install from the installer may or may not actually put the boot files onto the USB's EFI partition, so expect to copy them over from the hard disk's EFI, where they may wind up (/EFI/ubuntu ).  If you can get the --removable switch on the grub-install (maybe run it yourself), you will get a copy of the grubx64.efi bootloader put into /EFI/Boot/bootx64.efi, which is a good thing, because that is the default bootloader for removable media.  Or again, just make the directory and copy/rename it yourself.  The grub-install will not correctly set up /EFI/Boot for a secure boot, even if you give it all the switches which indicate a secure boot install is wanted, but again, just copy the shimx64.efi to the /EFI/Boot/bootx64.efi file, and also put a copy of grubx64.efi there too.
  Now, the beauty of this approach, is that the bootx64.efi is a standard UEFI bootloader name, so HP may actually work with it.  Doing the same setup on the hard disk's /EFI/Boot may have benefits, since that bootloader may be tried after a first boot failure, before the second bootloader in the boot order.  Otherwise, just play the usual games of renaming the Ubuntu bootloader to the Windows name, label like a Windows bootloader, and complain to HP about their non-standard UEFI implementation.;^)

---

### Post by oldfred on 2015-03-04
Some threads with HP installs. They all had to do work arounds.

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by matt18 on 2015-03-06
> **oldfred said:**
> Some threads with HP installs. They all had to do work arounds.

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

O...M...G

lol, why are manufactures doing this? do they not want people to have the freedom to choose what they want to do for themselves?

well, untill i figure out what i want to do, its either run it in vmplayer(still slow) or try it on a usb flash drive

Thanks for all the pointers and advice. Took me a while to reply, had a strength of materials test had to study for. glad it is the weekend haha

---

### Post by oldfred on 2015-03-06
> strength of materials test

That was so 50 years ago for me. :)

But Engineering Open house was always good. They made 3 Million pound concrete columns to break in their test machine. I was going to do Fluid Mechanics but Advanced Differential equations was a bit much. Back then it was all manual, if I knew computers would do all that I may have stayed with it, but switched to IE and used computers a lot.

---

### Post by matt18 on 2015-03-09
> **oldfred said:**
> That was so 50 years ago for me. :)

But Engineering Open house was always good. They made 3 Million pound concrete columns to break in their test machine. I was going to do Fluid Mechanics but Advanced Differential equations was a bit much. Back then it was all manual, if I knew computers would do all that I may have stayed with it, but switched to IE and used computers a lot.

LOL, yeah what was 50 years ago for you is now present for me. Its an amazing class. See i never took any physics or science classes in high school (2003). My highest math class was alg. in high school. 8 years went by and i could hardley add fractions 4 years ago. i mean i placed in math 2 below the gen ed requirement, now im done with linear algebra and diff eq. 

My point is, this stuff is soo new to me that i have a hard time "believing" it haha

Ok, question for the forums. I have made my decision to install lubuntu onto a USB 3.0 flash drive to use for my laptop. This is not the pc experiencing the issues in the previous thread where lubuntu is not seeing the hdd. that is a desktop pc. 

will it be faster to run it live off of the usb or to have it actually install to the usb? what is the best option which allows for the smoothest and fastest exp? haha. im choosing lubuntu because it is lieghtweight and the unity launcher is not my fav. i like a docky or cairo haha. 

thanks

---

### Post by oldfred on 2015-03-09
If you want to be able to do updates or make changes, you need to do a full install. 
Flash drives do not last forever, but should be good for a while. USB3 ports and USB3 flash drives are faster and with some settings to reduce writes can be very functional if not speedy.
Ubuntu does cache activity in RAM so no matter how you install drive is not read as much if not changing major applications a lot or have lots of RAM.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

