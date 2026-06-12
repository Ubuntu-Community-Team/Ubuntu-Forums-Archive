---
title: "Defeating UEFI on new Windows computer"
date: 2016-06-22
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2016-06-22
I know there's vast information on this (too much, actually, of varying ages and reliability).  I need a simple, quick answer--not just being lazy.

I'm forced to get a new Windows computer.  It will 7 or 10, probably Dell, and probably with Intel graphics.  I'm looking to defeat the UEFI nightmare easily and enable dual boot with Ubuntu.  I want to do this combat once and only once.  Thereafter I should be able to just turn the computer on, with no special boot procedures except for choosing the OS at boot time.

Will I be able to do this?  Is it a horrendous experience?  Any gotchyas to watch for?  I'm looking for simple, short answers pointing me in the right direction.  I can look up details.

---

### Post by QIII on 2016-06-22
Why go through the effort of "defeating" when you can just do a UEFI installation?  There are a couple of settings to change and then you install.

There's nothing to "defeat".

---

### Post by Geoffrey_Arndt on 2016-06-22
Well, the easiest way (by far) is just to buy your new computer with Win 7, 8, or 10 AND Ubuntu pre-installed.   

 Then, the setup takes maybe 5 minutes to do, and you can be as lazy as you want.   See the list in my signature, . . . BUT, you have to let the vendor know you want a dual-boot system, and then be prepared to pay extra for it.

---

### Post by oldfred on 2016-06-22
As QIII mentions, if you do a few settings in UEFI and Windows before hand and make sure you install Ubuntu in UEFI mode, you will not have any issues.

       Summary UEFI install instructions:
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit installer, flash drive or DVD.
Use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot.
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

### Post by Geoffrey_Arndt on 2016-06-22
Good info OldFred . . nice summary, thereby making a UEFI install less intimidating.   As my newest PC (circa 2015 System76 Galago laptop) did not come with UEFI (but MBR) based bios, I have zero personal experience with UEFI installs.   But here are a couple quick questions I hope to get some clarification on:

 >  ?? Is it not needed (using this method) to setup small 5 MB partition for efi boot manager ?? 

   >  ??  Does the "Something Else" install process still display & require where to install grub2?   Is that option still offered or is it superfluous with this install method (e.g., grub2 not really needed to dual boot under uefi) ??

---

### Post by oldfred on 2016-06-22
The ESP - efi system partition is required (FAT32 with boot flag) and you should only have one per device, although some UEFI will support more than one, and some more complex boot schemes may need more than one. Windows typically makes ESP 100MB, but we suggest 300 to 500MB unless on a small drive, like a flash drive.

The bios_grub is a 1 or 2MB unformatted partition for BIOS/CSM/Legacy boot with gpt partitioning, whether sytem is UEFI or BIOS.

The Something Else install option nicely displays grub boot loader install location. And it is a crock.
Grub only installs to the ESP on drive seen as sda. If sda does not have an ESP, it will not install. And if installing to any drive other than sda, it overwrites the /EFI/ubuntu folder in sda's ESP. My second install to sdb even said installing to sdb, but overwrote my main working install settings in sda's ESP. Or if multiple Ubuntu installs be sure to backup ESP before installing.

---

### Post by VanillaMozilla on 2016-06-22
Thanks, guys.  It sounds straightforward enough (I hope).  I'll probably go for it in the near future.

QIII, by "defeat", I mean "negotiate with", "capitulate to", "live with", "eliminate", "nuke", or "conquer".  Anything just so it doesn't defeat me.

---

### Post by Geoffrey_Arndt on 2016-06-22
For the best odds, consider an "all Intel" Dell system.   That is, intel cpu, graphics & wireless.   (unless of course gaming is an area of importance).    Dell seems to do a better job at complying with uefi standards.    Also, there are the new small form factor desktops such as the CL100 from Logic Supply, . . . they will configure the unit any which way you want:   [http://www.logicsupply.com/](http://www.logicsupply.com/)

---

### Post by VanillaMozilla on 2016-06-24
Just one more question.  There isn't any special procedure to boot, besides choosing the system at boot time, is there?  I wouldn't want to have to get into UEFI settings or supply a UEFI or BIOS password or anything like that.

---

### Post by ubfan1 on 2016-06-25
Just select the system and it should boot.  All the secure boot key business is totally hidden with standard Ubuntu installs.  Some older firmware might have gotten the standard UEFI key processing mixed up (like Toshiba version 6.5 and earlier, but that was fixed 2012.

---

### Post by VanillaMozilla on 2016-06-29
OK, thanks.  Cleared for purchase, any time now.

---

