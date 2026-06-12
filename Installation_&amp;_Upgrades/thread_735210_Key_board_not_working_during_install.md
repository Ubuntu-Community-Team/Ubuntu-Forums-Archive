---
title: "Key board not working during install"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by hds17 on 2008-03-25
Hi All,

I am trying to install desktop 7.10 for a Dell Dimension E520.  When the Ubuntu install screens comes up,  my key board does not work.  I can not select any options.  Has anyone had this happen? if you could point me in the right direction I would be much appreciative.

Regards,

MM

---

### Post by buntu_Geek on 2008-03-25
First of all... the bios wont allow a boot when devices like keyboard is not working....

So i would suggest you to check the connection of your keyboard....

And is your keyboard a ps2 type or usb ???

---

### Post by hds17 on 2008-03-25
Keyboard is an USB Dell Key Board.  It works during the initial boot up,  I can go into set up.  However as soon as the Ubuntu Logo comes up with a list of options like "Install to hard disk"  the key board is does not function.

---

### Post by confused57 on 2008-03-25
> **hds17 said:**
> Keyboard is an USB Dell Key Board.  It works during the initial boot up,  I can go into set up.  However as soon as the Ubuntu Logo comes up with a list of options like "Install to hard disk"  the key board is does not function.
Go into your bios setup & see if there an option something like "usb legacy" that you can enable.

---

### Post by Pumalite on 2008-03-25
Another thing you can do is just change the keyboard to a different port after boot.

---

### Post by stellar22 on 2008-03-25
I believe I'm experiencing the same problem. Actually, after I get to select the language (English) and Ubuntu goes through initializing the installation, my computer freezes when selecting the language once more. I initially thought it was the keyboard and mouse that suddenly stopped working but the numlock key would not respond so I believe the computer froze on me.

I've had this problem ever since I installed Gutsy over WindowXP and configured it to dual boot. The first  time worked but I could no longer downgrade Ubuntu from i686 to i386. I always encounter the same problem using the normal or alternate installers. I tried both installers for Hardy Beta and those just do the same thing.

Does anyone know what can help? I've already configured dual-boot but I'd like to downgrade to i386 or upgrade to Hardy i386 without having to reformat and start everything from scratch. Information below might help:

OS: 7.10 Gutsy for AMD64 (using GRUB to dual boot in WinXP)
Partition: 195GB Ubuntu (Primary) - 92GB NTFS WinXP (Logical) - 996MB Ubuntu Swap (Primary) - 8.88GB HP Recovery Partition (Primary)
RAM: 2GB
CPU: AMD64 X2 4400
Model: HP Pavilion a6202n

Sorry for the long post but I thought it would help to provide all the background info. There might be something with my dual-boot setup that is causing all this mess since it worked the first time.

Thank you.

---

### Post by buntu_Geek on 2008-03-25
There can't be a downgrade from i686 to i386... because of many reasons...

When the architecture differs, every single program or application on your hdd must be replaced with the respective architecture binaries... even the kernel...

So even if there is such an option called downgrade from i686 to i386.... it would fully replace all the apps and stuffs...

---

### Post by buntu_Geek on 2008-03-25
@ hds17..

I also recommend what Pumalite suggested....

---

### Post by stellar22 on 2008-03-25
> **buntu_Geek said:**
> There can't be a downgrade from i686 to i386... because of many reasons...

When the architecture differs, every single program or application on your hdd must be replaced with the respective architecture binaries... even the kernel...

So even if there is such an option called downgrade from i686 to i386.... it would fully replace all the apps and stuffs...

OK I can work with a complete reinstall of Ubuntu if I can get that far :D Any ideas why the computer freezes when running the Ubuntu (Gutsy/Hardy i386/i686 normal/alternate) installers? I've downloaded all versions of installers for Gutsy and Hardy on both architectures. Could it be my partition setup? If I choose to reinstall completely will it require me to touch the WinXP?

Thank you.

---

### Post by buntu_Geek on 2008-03-26
I think you downloaded and burnt only the amd 64 bit version of ubuntu..????

It should not be i686 or i386,,,, !!!!

---

### Post by IanVaughan on 2008-03-26
This one has been annoying me since 7.10, and now with 8.04 still not resolving it, I would like this to be known about.

Standard Dell Dimension, with Dell USB keyboard, with normal ubuntu download, the boot menu will not allow keyboard inputs.

The menu then times out with the install/live cd option, after which when booted the keyboard works fine.

This was working in 6.10, and I dont have a legacy option in the BIOS.

---

### Post by DellCA on 2008-03-27
On older Dimension desktops there is a USB setting in the BIOS that could effect how the keyboard works.  In the "Integrated Devices (Legacy Select)" section of the BIOS there is a "USB Emulation" option.  If it is not already set to "ON" try that and see if it allows you to use the keyboard.

Other Dell desktop models have a similar option, but it is not always in the same place.  If anyone else is having trouble finding it, just let me know what model Dell you have and I'll be glad to find it for you.

Larry
Dell Customer Advocate

---

### Post by deathguppie on 2008-03-27
The Dell Dimension E520, the same one that comes with Ubuntu preinstalled does not have that option in the bios.  In fact the only USB option available is a no-boot option that disable's the bootable flag from USB.

I tried it, simply because it was the only option available, and no go.

The issue is with grub.  Not the linux USB subsystem.  The light is on so I know that the keyboard is available it is just that grub cannot connect to it.

Previous versions of grub do however work, and the answer seems to be to mount the ISO and replace grub with and older version.  I'm not even going to try to explain here all that involves, but if you are having this issue don't worry because Ubuntu defaults to booting into the liveCD. 

 Although the devs should really look into fixing this.

---

### Post by IanVaughan on 2008-03-28
But if it was Grub, would not the same problem exist after install with the OS select menu?

I am not at my PC right now, but I have tried changing USB settings in the BIOS, and none (I think only 2 USB related options were present) allowed the CD Boot menu to allow keyboard selection.

And the above comment stating with the keyboard light is on, this is not the case for me. Caps/Num Lock do not change the light status, which remain off.

If DellCA could confirm the bios option for a Dell D5150, I will give it a go. (What about BIOS version as well! Again as not at home I cannot confirm my current version.)

---

### Post by DellCA on 2008-03-28
I went and double checked and you are correct, there are no USB emulation/legacy options on the E520.  This means that it should check for USB keyboard/mouse connection and use that by default.

If the keyboard works when booting from the LiveCD, but not for any other option it sounds to me like it is something with the USB drivers for the kernel that are the problem.  I'm not that familiar with Ubuntu (I use Gentoo at home) but you might want to check the kernel configuration to make sure all of the correct USB options are enabled.

It might be something else that causing the problem but, unfortunately, I'm not sure what else it could be.

Larry
Dell Customer Advocate

---

### Post by drhiii on 2008-04-25
I too have an E520 and I tooo cannot get 7.10 to install any way I come at it.  Same USB problem.  

Any progress on this?  I know it has been a problem for quite awhile.




> **DellCA said:**
> I went and double checked and you are correct, there are no USB emulation/legacy options on the E520.  This means that it should check for USB keyboard/mouse connection and use that by default.

If the keyboard works when booting from the LiveCD, but not for any other option it sounds to me like it is something with the USB drivers for the kernel that are the problem.  I'm not that familiar with Ubuntu (I use Gentoo at home) but you might want to check the kernel configuration to make sure all of the correct USB options are enabled.

It might be something else that causing the problem but, unfortunately, I'm not sure what else it could be.

Larry
Dell Customer Advocate

---

### Post by letubenaiah on 2008-04-25
I'm having the same problem trying to boot the 8.04 liveCD as well.  The USB keyboard works just fine until I get to the select language screen and then it stops.  I'm also using a Dell E520, with a Dell keyboard.  

Benaiah

---

