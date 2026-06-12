---
title: "Can't boot Ubuntu 12.10 properly on a USB Stick"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by Gobtron on 2013-04-20
Hi.

I bought a new Lenovo y400 pre-installed with Windows 8. I want to remove Windows 8 and do a clean install of Windows 7 (x64) and Ubuntu 12.10 (x64) using UEFI capabilities.

So I made a bootable USB drive of Ubuntu 12.10 (x64) with Pendrive.

I am in UEFI boot mode, secude boot is off. I had problem before with the UEFI boot mode, but now I can finally boot from the usb device. 

The problem now is that when I choose the option "Try Ubuntu without installing", I get stuck at the black screen. So I edited the commands and added "nomodeset" after "quiet splash". I see something on the screen, but it's all glitchy, can't do anything with that.

What can I do to solve the problem? 

Laptop specs:

Nvidia GT 750M 2GB
Inter i7 3630QM
8gm ram
1tb (in UEFI boot mode)

---

### Post by oldfred on 2013-04-20
Is this an UltraBook?
That has both nVidia and Intel graphics which cause issues. Once installed you can then install Bumblebee to make it work.
I think most have to turn nVidia off to get it to boot.

Some other comments:
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)


 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by Gobtron on 2013-04-20
> **oldfred said:**
> Is this an UltraBook?
That has both nVidia and Intel graphics which cause issues. Once installed you can then install Bumblebee to make it work.
I think most have to turn nVidia off to get it to boot.


I have a Lenovo y400 (14") with the specs mentioned above. I don't know if you can call this and Ultrabook?

So I understand that the glitches are caused by the fact that I have switchable gpu in my system. So how can I ignore the Nvidia in grub?

I also have the same problem with Windows 7... I can get it to boot, but it can't get past the "Windows startup" screen. But one thing at a time :P

---

### Post by oldfred on 2013-04-20
I think it is a UEFI/BIOS setting. The in grub you use nomodeset if nVidia or usually Intel works but some of the new Intel seem to require the default monitor size to be set in grub to make it work.

I think I saw somewhere that Microsoft was not writing new drivers for Windows 7 to use for any new features with new systems running Windows 8. Or in effect you cannot go back. Some have posted they have installed Windows 7, but early Windows 8 systems that did not have any real hardware changes over the Windows 7 models. I think Windows only boots in UEFI mode from flash drive, not DVD.

       Force Intel Video mode as boot parameter in grub menu, but use your default size or in grub command line run this to see supported modes.
      
 From a grub command line to see available settings
vbeinfo

    
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by Gobtron on 2013-04-20
> **oldfred said:**
> I think it is a UEFI/BIOS setting. The in grub you use nomodeset if nVidia or usually Intel works but some of the new Intel seem to require the default monitor size to be set in grub to make it work.

I think I saw somewhere that Microsoft was not writing new drivers for Windows 7 to use for any new features with new systems running Windows 8. Or in effect you cannot go back. Some have posted they have installed Windows 7, but early Windows 8 systems that did not have any real hardware changes over the Windows 7 models. I think Windows only boots in UEFI mode from flash drive, not DVD.

       Force Intel Video mode as boot parameter in grub menu, but use your default size or in grub command line run this to see supported modes.
      
 From a grub command line to see available settings
vbeinfo

    
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

Nope... didn't work.

"vbeinfo" doesn't work either. Unknown command...

---

### Post by Gobtron on 2013-04-20
Damn it... I've been on it all day... still no progress. 
It seems that I cannot use a custom resolution and refresh rate. It seems that I can tell GRUB not to use Nvidia card, but cannot set the resolution. The glitches look like a bad resolution or refresh rate...

Is it possible that when you use nouveau.modeset=1 (wich I do, so I don't have the black screen), you can't specify a costum resolution ??

---

### Post by oldfred on 2013-04-20
Since you have grub with UEFI, does it show a gfx setting.
I believe it usually is set gfxpayload=keep
But you should be able to set something.
 gfxmode=640x480
Change to whatever works?

---

### Post by Gobtron on 2013-04-22
Ok so I got rid of the glitches. 

I had to modify grub.cfg and replace "set gfxmode=auto"   by   "set gfxmode=1366x768"

and put the "nomodeset=1" argument in the linux command

For some reason that was not working when i wrote those in the grub line editor (typing "e" in the menu)


BUT


I hear that weird mid-pitched noise coming from my laptop?! What is that? I am afraid! It is a continuous sound, not coming from the speakers.

It seems that I could probably go through the installation process though... Well at least it loads the graphical installation and things seem to work (didnt go far, since i hear that noise)

So.. Should I just ignore that sound and complete the installation until it can load nvidia drivers?

By the way, I have a GT 750M (with Optimus technology)

---

### Post by oldfred on 2013-04-22
The only whining noise I ever get from either system is the DVD spinning up. Not sure what your are getting?

 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

---

### Post by Gobtron on 2013-04-22
There's no DVD in the tray... It doesnt seem like a dvd noise.

I don't know how to describe... that's just weird. I should record it somehow.

---

### Post by oldfred on 2013-04-22
After I mucked around in my desktop one time I had some noises, but a wire was touching a fan. 
Also found I have to clean system as fan works as a good vacuum cleaner and it retains a lot of dust and crud.

---

### Post by Gobtron on 2013-04-22
Yah, but I currently run Win8 without any weird noise, and I got the laptop, brand new, 4 days ago, so I don't think I have a dust issue.

---

