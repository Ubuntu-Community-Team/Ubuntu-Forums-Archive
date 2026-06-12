---
title: "Computer won't install Ubuntu on blank drive"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by mikah2 on 2015-10-24
I just finished a computer build, I'm trying to install Ubuntu 14.04 but at first every time I selected install from the GRUB menu the video signal would drop and never come back up, after clearing out the USB and putting everything back when I go to install it never reaches the GRUB, it pops up with a fullscreen terminal with a blinking line and I can't do anything, sometimes it comes up with an error about having no bootable OS, but more often it just sits there for hours doing nothing.
Sorry if this is reposted, I looked for other posts but nothing seemed to fit my problem.

---

### Post by ubfan1 on 2015-10-24
What video hardware do you have?  Nvidia tends to want the "nomodeset" option (one of the function keys you select before selecting "install" or "try".

---

### Post by mikah2 on 2015-10-24
I do have nvidia, and I have the guide for solving the video issue when it pops up, but I can't get to the menu to select install.

---

### Post by yancek on 2015-10-24
What software are you using to put the Ubuntu iso on the usb drive you are booting from?  Maybe it didn't work.  Do you have another computer you can try booting it from to elminate that as a possible problem?

---

### Post by mikah2 on 2015-10-24
I'm actually unsure, I just used the install guide I found on google. First I created a bootable usb on windows, then I tried to install and that's I encountered the video problem, at this point I had already moved my laptop from windows to ubuntu using the same usb, thinking I may have messed up the usb I cleared it and made a new bootable with the startup disk creator. At that point is where it started not getting to the menu These are the only two computers I have.

---

### Post by buzzingrobot on 2015-10-24
If nomodeset is used correctly, it should boot into a degraded, but usable, display. The open source Nvidia driver can't handle some Nvidia cards, so you may need to use nomodeset after the install until you install a proprietary driver, preferably via "Additional Drivers&.

The " no bootable OS" makes me suspicious of the USB.

---

### Post by mikah2 on 2015-10-24
Is there something I may have messed up in making the USB bootable, because when I first tried it I used the guide to make it on windows, then I checked it by installing on the laptop I made it with, when I started encountering problems was when I cleared the drive and made a new bootable. So should I try making it again, is there another way to check them without actually installing on anything?

---

### Post by sudodus on 2015-10-24
You can check with md5sum that the iso file is good. It should match the value found via

[UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

There are several tools to use, if there are problems with the Ubuntu Startup Disk Creator. You can start with the following link and links from it

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And yes, [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by mikah2 on 2015-10-24
So I spent the past few hours trying every combination I can to get it to boot, I can't get anything to work, the live usb is fine, and installs any version I put on it, just not on my new computer, it's always the blank terminal, or it says something along the lines of not bootable, please restart or insert media and press a key.

---

### Post by Geoffrey_Arndt on 2015-10-25
>   What is your PC make and model & specs? (ram, cpu, mobo,hdd types, video chipset, wireless chipset)?
>   What (if any) OS is on the PC?  Win 7, Win 8, Win 10?
>   What specific program did you use in Windows to create bootable usb stick (for instance, "Pendrive Linux")?
>   When you say you "cleared" the drive, what does that mean?   That you erased or formatted the drive?
>   Did you check Windows bios/uefi to see if usb device boot up is selected?   Important to verify if PC is uefi.
>   Did you shrink the Windows partition?  Or did you remove/erase Windows or any Windows files?
>   Did you create a linux partition and/or do you have unallocated space?
>   Am assuming you used the windows tools to do the step above (not creating part - but the shrinking partition part)
>   Did you turn off "secure boot" in Windows?
>   Did you turn off fast/quick boot in Windows?
>   Did you disable Windows hibernation?
>   So, am assuming you've seen none of the standard ubuntu install screens (time zone, user setup, etc.)?   Because the "try ubuntu" or "install ubuntu" screen never shows up?

---

### Post by mikah2 on 2015-10-25
Custom build
2 x  gb patriot viper 3, amd fx 8350, gigabyte 990fx ga ud3, 1 seagate 2 tb hybrid, gigabyte gtx 970 windforce, unsure on wireless, built in with mobo I think.
No OS on it
I've tried both the startup disk creator and unet.
Erased then formatted
It is set to boot from USB and to accept either legacy or uefi.
blank drive.
And I got to that menu once, with the install I created while using windows, but in the intervening time I upgraded my laptop to Ubuntu and have sine been using the tools available for it.

---

### Post by mikah2 on 2015-10-25
I don't know how to mark as solved, but I finally got it to work.

---

### Post by mikah2 on 2015-10-25
Well I thought it was solved, I got it to install, now when I boot it loads to purple screen then I lose video signal and an't get it back.

---

### Post by sudodus on 2015-10-25
> It is set to boot from USB and to accept either legacy or uefi.

Maybe it works better if you select a setting of either legacy (BIOS, CSM) or UEFI.

It is good that you answered many of the questions in post #10. Please try to answer all of them, it makes it easier to help.

And another question from me now, (I'm not sure if it was asked or replied before).

- Does the computer work at all or work well, when booted from a USB pendrive with Ubuntu, 'Try Ubuntu'?

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by kurt18947 on 2015-10-25
> **mikah2 said:**
> So I spent the past few hours trying every combination I can to get it to boot, I can't get anything to work, the live usb is fine, and installs any version I put on it, just not on my new computer, it's always the blank terminal, or it says something along the lines of not bootable, please restart or insert media and press a key.

I have one PC that is something like what you're experiencing. I'd format USBs to FAT32 using gparted, create the USB using Unetbootin and it would boot in every machine I tried - except one. What I discovered is that if I formatted the USB with **Windows** then proceeded with Unetbootin the USB would boot fine. It seems there's something in the boot portion of that one machine's BIOS that looks for something specific to Windows FAT32 formatting. Booting from a CD/DVD (UDF file system?) is not affected.

---

### Post by sudodus on 2015-10-25
> **kurt18947 said:**
> I have one PC that is something like what you're experiencing. I'd format USBs to FAT32 using gparted, create the USB using Unetbootin and it would boot in every machine I tried - except one. What I discovered is that if I formatted the USB with **Windows** then proceeded with Unetbootin the USB would boot fine. It seems there's something in the boot portion of that one machine's BIOS that looks for something specific to Windows FAT32 formatting. Booting from a CD/DVD (UDF file system?) is not affected.

This is interesting. Maybe you can check what is different as seen via gparted and also via a binary (hex) editor :-)

-o-

I have found that the ***flag*** on the boot partition can make a difference.

It can also make a difference if the pendrive is ***'clean'*** before making the partition table and file system, and often it is enough the 'wipe' or overwrite the first megabyte with zeros.

Booting from CD with the Ubuntu family iso file uses the ***ISO 9660*** file system. This is also the case if you copy/clone/flash the iso file to a USB pendrive with cp, dd or a GUI tool, that uses that method under the hood.

---

### Post by Geoffrey_Arndt on 2015-10-25
So, here's something to consider:   

 Does the PC have optical disk reader?   IF so, let's move on to that and just get the install done.  IF NOT, then, you can get an inexpensive dvd/cd RW device from Amazon (Amazon Basics USB 2.0External Slim DVD Writer - SIN:  B003MONT1M - Tested with Ubuntu 15.04).   I think I paid less than $30.00 for that device.  Works perfect on my System76 Galago laptop.

---

### Post by mikah2 on 2015-10-25
The way I got it to work was to use uefi only and only the usb 3.0 port nearest the motherboard, the other port stacked above it and the one on the case, as well as all the usb 2.0 ports wouldn't work.
Now I used nomodeset to do the install and it worked, but after the restart it loads a purple screen then the video signal cuts off, I can use the usb to boot with try ubuntu and nomodeset but I an't get my internet connection to work, I have no wireless built into the mobo like I thought, so I used a hardline but it still won't connect.

---

### Post by Geoffrey_Arndt on 2015-10-25
Remember, you can use one-time nomodeset just to get you into the OS - - THEN - - you have to immediately download the proprietary nvidia drivers via the additional drivers tab in the software & updates program.   Then, you will be able to reboot into the system.

For internet access, looks like you'll need to get a usb wireless adapter like Panda ultra 150 b/g/n (about !0$ on amazon).   Panda makes 2 or 3 wireless adapters that are tested with Linux and in particular, Ubuntu.

---

### Post by mikah2 on 2015-10-25
But the hardwire connection doesn't work either, I found the realtek driver for my mobo but I can't get it to install.

---

### Post by Geoffrey_Arndt on 2015-10-25
Well, with a system that's borderline "crippled" . . . it's going to be a challenge to "build"/"compile" any driver (even winders).   You may not have the "build-essential" package installed (from the iso image source), and if you don't have any internet any which way . . . . well.    I'm kinda out of my area of experience at this point.    

After installing various flavors of Linux (about 15 or so different distros) . . . . I'm now at the point where I just buy pre-installed Linux hardware off the net.   Gives the user the total opposite result of what you've experienced so far.    

My last suggestion (just a stab in the dark) . . . the mobo should have all that's needed for ethernet and wireless (with an adaptor).   The ethernet thing is fixable via the networking tools in Ubuntu but I don't have a cheat sheet of the bash coding as my ethernet has always worked automatically (on 20+ computers).   The risk is low ($10 usd) for getting a compatible adaptor & trying it out -- no drivers to install with the Panda devices.  (and it would work with other/future hardware as a backup tool).   Unless you can get networking to work, Ubuntu is even more useless than a Chromebook (if that's even possible!).

Looks like we'll need more experienced help from the network sme's here at the boards.

---

### Post by mikah2 on 2015-10-25
I found that my motherboard is prepakaged with windows drivers, I have the drivers on a drive I can access if I boot from the USB and pick try Ubuntu, I just don't know how install them or move them to where they install when I boot without the USB.

---

### Post by mikah2 on 2015-10-25
Every time I solve one problem, another one pops up.
Current problem, can't login, anytime I put in password it pops up what looks like the tty alot of text is input and it cuts back to the login screen. I can enter tty and login, but when I exit it goes back to login screen

---

### Post by Geoffrey_Arndt on 2015-10-26
Windows drivers are not going to install in a Linux system . . . Windows exe's are not runnable or installing in Linux without 3rd party wrappers or emulators.   On an installed Ubuntu, a VM (virtual machine allows for install of the Windows OS as a guest operating system - - but that's not remotely possible on this system).     I'm at a loss as to next steps other than trying a full reinstall using a DVD.   It would also be easier (because of lesser graphics requirements) to install a version of Ubuntu such as Xubuntu or Ubuntu Mate rather than Ubuntu with Unity desktop.   But I wouldn't even do that until I had in my hand the wireless usb adapter so you have a better choice of internet connectivity.

---

### Post by Vladlenin5000 on 2015-10-26
Your main problem right now is not having internet access and the reason you don't have a properly working Ethernet (and some USB ports) is due to the infamous IOMMU problem your board has.
So, first of all disable IOMMU in BIOS/UEFI. Then edit GRUB and add "iommu=soft" in the same line you added *nomodeset *(yes, you need both until you have the proprietary nvidia drivers installed). 
Doing this your Ethernet should work OOTB as well as all your onboard USB hubs. Proceed to install the recommended proprietary driver, reboot, re-edit GRUB to remove nomodeset but keep the iommu=soft. Done!

---

### Post by Geoffrey_Arndt on 2015-10-26
Excellent research Vladlenin5000!!   

I have to save and send this to a PC club member that wants to build a Linux PC . . in case he gets the same MOBO.   This should now give Mikah2 a much improved chance to finish a successful install.

---

### Post by Vladlenin5000 on 2015-10-26
AFAIK the problem occurs only in boards with the AMD970 chipset and it varies depending on brand/model. In some like my MSI Gaming it only affects USB3.0 ports (onboard or addon card) while others like Gigabyte present the same symptoms as described here. It's horrible and it must be done in any install until someone tackles the issue for good.
It took me many hours to research and test, indeed. The information is scattered in a few threads and nowhere it's written like I did in the previous post: This is the problem and here's the workaround. Instead it's pages after pages of well intentioned people doing the best they can to guess... Of course, who would have though a Linux specific "feature" was the culprit?

---

