---
title: "Install from usb does not complete: grub screen appears ok"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by inigodenoriega on 2015-07-28
Hi

I have recently bought a new PC, with no operating system pre-installed. I have installed Win7 with a usb key, with no problems. I created an installation usb for Ubuntu 14.02.2 LTS, and the GNU-GRUB screen (version 2.02-beta2-9ubuntu1) shows us correctly, with the following options:
-Try Ubuntu without installing
-Install Ubuntu
-OEM install (for manufacturers)
-Check disk for defects

I have tried both of the first options, after selecting them, the screen turns black and then... nothing. So far, I have ignored the other two options, as they are not what I'm looking for, and since the screen shows up correctly, I consider that the usb key works correctly.

The usb key has been created both in Ubuntu (another PC) and Windows, and in both the GNU GRUB screen shows up correctly, but after selecting an option, the screen goes black and the installation does not continue.

The PC has an SSD drive in which I have Win7 OS and wish to install the Ubuntu OS, leaving the larger HDD drive for personal files. Could this have anything to do with this?

I have previously installed Ubuntu in other PCs with no issues, but with PCs with pre-installed windows. In one case, with two "conventional" HDs, and have not encountered these issues.

Any ideas? I really want to install Ubuntu in the PC as I have in previous computers.
Thanks in advance

---

### Post by tomasrey88 on 2015-07-28
Same thing happened to me just now. **Check to see if you have the correct version of Ubuntu**. 32 bit Ubuntu for 32 bit computers and 64 bit Ubuntu for 64 bit computers. If you mismatch, it will not work. For example, I used 64 bit Ubuntu (linux mint, just a prettier ubuntu) disk to install on usb, then when plugged into a 32 bit computer, nothing happened.

[B]shameless plug: 
answer my question (thanks!)[/B]
[http://ubuntuforums.org/showthread.php?t=2288606](http://ubuntuforums.org/showthread.php?t=2288606)

---

### Post by oldfred on 2015-07-28
Black screen is almost always a video issue.
What video card/chip does system have?

If nVidia or AMD nomodeset usually gets you into  a lower quality video. If Intel it needs its own settings.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If new system hardware is usually UEFI. Did you install Windows 7 in BIOS or UEFI boot mode?
How you installed Windows UEFI or BIOS is how you want to install Ubuntu.
Post this:
sudo parted -l

Windows 7 default install seems to be only BIOS, you have to copy  installer to flash drive and move some efi boot files into an efi folder for UEFI boot.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by inigodenoriega on 2015-07-29
Hi Tomas, thanks for the quick reply. :KS
I realise that I did not include enough information in my description. I have a 64-bit computer, and have indeed downloaded the 64-bit Ubuntu installer, so I don't think that should be the issue.

---

### Post by inigodenoriega on 2015-07-29
I have a Gigabyte GeForce GTX 960 Windforce OC 2GB DDR5 graphics card, it's nVidia.

I don't know in what mode I installed Windows (BIOS or UEFI).

When I start the computer, the screen with the keyboard logo and the man ([https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)) does *not* appear, it boots directly into the gnu-grub screen without the "Ubuntu" text and logo, nor does it have the F1-F6 options below nor the "boot from first hard disk" option. I have tried pressing keys before the GNU-GRUB screen showed up, but it loads the same screen. Maybe this is because I'm using a USB key instead of a CD/DVD?

In any case, as I was writing the post, I tried the first link in your message, the Nomodeset one. Despite being unable to see the image of the screenshot, I tried several options: the one that works is inserting nomodeset as follows "[...] quiet splash **nomodeset **--" and pressing F10 (in my computer CTRL-X just types an "X"). And then... Ubuntu screen logo! I'm currently setting up the wireless, so the installation seems to go fine.

Many thanks! :-)

---

### Post by oldfred on 2015-07-29
If you get grub menu at boot, then that is UEFI boot. Purple screen with f keys is BIOS boot.

But then it matters a lot how you installed Windows. If in BIOS mode you may have issues.

Post this:
sudo parted -l

---

