---
title: "&quot;No Root File System Defined&quot;"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by mom4bengmail.com on 2015-10-06
I am installing Ubuntu 14.04 with WUBI, and during the installation I get.
"No Root File System Defined" (as superuser)
I've done research and they all say put a "/" in the partitioning menu.

   Thing is I don't have that option, all I have is the windows saying
"Fix this error in the Partitioning Menu."
So I don't have the partitioning menu open, just that window.
I'm running Windows 7

Any help will be appreciated. [IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

(and tell me if I posted this in the wrong section)

---

### Post by hakuna_matata on 2015-10-06
> **mom4bengmail.com said:**
> I am installing Ubuntu 14.04 with WUBI, and during the installation I get.
"No Root File System Defined" (as superuser)

Is it really Ubuntu 14.**04** ? If it is Ubuntu 14.**10** or above, it is [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") which only affects Wubi installations and a **recommended** standard installation without Wubi should work.

If it is Ubuntu 14.04, maybe it is a more serious issue with recognizing your hard disk. For diagnosis you can boot with Wubi into desktop iso. If you see
```
Completing the Ubuntu installation.
For more installation boot options, press `ESC' now...
```
press ESC and after that select
```
Demo mode
```
This should boot into a live enviroment where an installer for a standard installation is also available. But please open a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and type
```
sudo parted -l
```

---

### Post by mom4bengmail.com on 2015-10-06
Sorry about that, I downloaded the latest version of Ubuntu, which is 15.0 or something.

Maybe I need to edit something in my Disk Management? I might not have enough room to install Ubuntu.

---

### Post by hakuna_matata on 2015-10-06
> **mom4bengmail.com said:**
> 
Maybe I need to edit something in my Disk Management?
IMHO this doesn't solve the issue. We found a [workaround]("http://ubuntuforums.org/showthread.php?t=2251986") but a Wubi installation is **not** **recommended**. Did you try a standard installation, too ?

---

### Post by mom4bengmail.com on 2015-10-06
> Did you try a standard installation, too?

 Sorry I am not informed on what you mean by "Standard Form."
  I'm still a newbie at this so I don't know you mean by that.
Do you mean like a disk or a USB drive installation?

Or something else.

---

### Post by hakuna_matata on 2015-10-06
In your case I mean a [Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot") without Wubi.

---

### Post by oldfred on 2015-10-06
Last supported version of wubi is 12.04. Wubi was intended for ease of installation with Windows installed in MBR mode. Now only a few advanced users can install it and make it work.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

With UEFI and now gpt partitioning adding partitions is a lot easier. But Windows use of secure boot and having both BIOS & UEFI makes install a bit more complicated.

Best to use Windows own tools to shrink the NTFS partition and reboot immediately as Windows has to run chkdsk after any size change.
Often best to have secure boot off in UEFI, and turn off fast boot in UEFI.
Turn off fast startup in Windows.
      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Then how you boot installer either UEFI or BIOS is how it will install. If Windows 8 or later installed by the vendor you will have UEFI and need to install Ubuntu in UEFI boot mode.

       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by mom4bengmail.com on 2015-10-07
> [COLOR=#000000]a Wubi installation is [/COLOR]**not [B]recommended.**[/B]
So you're saying I shouldn't install ubuntu with WUBI?

---

### Post by QIII on 2015-10-07
Yes.  Wubi is no longer maintained and has been abandoned by its developers.  They recommended discontinuation of its use when Windows 8.1 was released.

---

### Post by hakuna_matata on 2015-10-07
> **mom4bengmail.com said:**
> So you're saying I shouldn't install ubuntu with WUBI?
Yes, if there is no special reason why you want Wubi. But I don't want that you avoid Ubuntu without Wubi, too. IMHO, no Ubuntu is worse than Ubuntu with Wubi.

---

### Post by mom4bengmail.com on 2015-10-07
Alright, thanks for all the information. @hakuna_matata @Qlll and @oldfred

 Most likely going to order an Ubuntu Disk, hopefully that'll work.

---

### Post by QIII on 2015-10-07
Don't order a disk.  If you have a DVD writer and burning software, or a USB thumb drive, you can make your own installation media.

---

### Post by oldfred on 2015-10-07
Download from here:
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by hakuna_matata on 2015-10-08
> **mom4bengmail.com said:**
> 
 Most likely going to order an Ubuntu Disk, hopefully that'll work.

Hmmm. Why are you going to order an Ubuntu Disk ?

Theoretically, it is also possible to use the iso file which Wubi already downloaded. File path: C:\ubuntu\install\installation.iso  Maybe, the drive letter C: differs, if you select another drive letter for Wubi installation. If Wubi installation is finished, installation.iso is removed, but in your case it is not finished. 

I wrote "theoretically" because the wubi.exe on iso for 15.04 downloads iso for 14.10 and 14.10 has reached its [“end of life"]("http://http://www.ubuntu.com/info/release-end-of-life"). So you need an upgrade immediately after installation. Not really a good solution, if other solutions are available. 

But I don't know your real installation issue which happens if you try a dual-boot.
 
BTW: Before you give up and avoid Ubuntu at all, try [these Wubi versions]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na")

---

