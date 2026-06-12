---
title: "Failed Installation Help"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by s25w89 on 2014-04-19
I've spent some time looking for a solution to this issue but can't find anyone who's had the same problem.

When trying to install Ubuntu 12.04 on my refurbished 64-bit Asus X401A I got all the way to the very end of the installation process and it failed saying there was some problem with the grub (sorry for not being more specific). I was booting off a USB stick using unetbootin (I did this when I was trying out Mint 16 a few months ago on this same laptop and I had no issues whatsoever). The ISO file I used is the same one I'm using to run Ubuntu on my Mac's virutalbox. It works there without issue so I don't think it's a corrupt file. 

After turning off the computer and booting it back up in BIOS mode I can successfully get to the menu that gives these three options:

- Try Ubuntu without installing
- Install Ubuntu
- Check disc for defects

No matter what option I select I get a black screen. I tested the USB I used for Mint and it does the same thing. When I boot up without any USB I get a black screen with the following text:

[B]GNU GRUB version 2.00-19ubuntu2.1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> _[/B]

Is there any chance I can salvage this and install Ubuntu successfully? This is an awesome distro and I really want my backup laptop to have it installed. 

Any insight at all will be greatly appreciated!

---

### Post by ajgreeny on 2014-04-19
Could this be a UEFI problem?

You say "After turning off the computer and booting it back up in BIOS mode I can  successfully get to the menu that gives these three options:" etc etc. So:-

Have you still got the USB inserted?  If so remove it.
Did you install in BIOS mode or UEFI?
Is this a single OS machine or dual booting with windows?

---

### Post by s25w89 on 2014-04-19
Thanks for your response ajgreeny.

The bold text in the original post shows up when there is no USB inserted. When it is inserted the menu I described with the 3 options comes up. I believe UEFI and BIOS were already present - I didn't install either. I checked in BIOS mode to make sure UEFI was enabled, etc and all looks good. This is a single OS machine. 

Before the initial attempt to install Ubuntu I was able to run it without installing it, if that helps in any way.

---

### Post by ajgreeny on 2014-04-19
I think you are confused a little about my meaning of did you install ubuntu in BIOS or UEFI mode.  You are correct in that you did not install BIOS or UEFI, they are both firmware that is present on the motherboard of the computer; BIOS is the older legacy system, UEFI is the new system that is normally used on Windows 8 machines and those with no OS at all probably.

If you booted the USB install media in and therefore will have installed ubuntu in UEFI mode you need to have a small 100 - 200 MB partition as detailed in the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") so I think before we go any further I suggest you have a good read through of that info which may help you figure out what is wrong.

---

### Post by s25w89 on 2014-04-20
So I read through that documentation and I know now that I was booting Ubuntu via UEFI mode. I don't believe I need to create an EFI partition since I've booted in this mode several times with Mint 16 and Ubuntu before the first attempt to fully install Ubuntu the other day. 

Any other ideas? I really appreciate the help

---

### Post by s25w89 on 2014-04-26
After further investigation I've come to the conclusion that this is a hardware problem. I'm letting this one go for now.

Thank you for everyone's help!

---

### Post by oldfred on 2014-04-26
Even if your hardware if UEFI, it also has a BIOS mode, CSM. And how a system installs is based on how you initially boot the installer.
So if you boot the Ubuntu install in UEFI mode it installs in UEFI mode. But if you boot in BIOS mode it installs in BIOS mode. Best is more than one install you install all in UEFI or all in BIOS. If not the only way to boot is from UEFI menu and you may have to turn on/off UEFI or turn on/off BIOS/Legacy/CSM mode. Some auto switch.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

