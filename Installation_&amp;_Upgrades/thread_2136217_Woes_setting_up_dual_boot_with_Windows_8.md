---
title: "Woes setting up dual boot with Windows 8"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by jeffpas on 2013-04-16
Hi All,  I have an Ubuntu 10.4 installation boot disk, and all I'm trying to do is set up a partition on a new Windows 8 machine. I've used Gparted and set aside the space (unallocated), then installed Ubuntu but after rebooting, there's no grub loader!  It just boots directly to Windows 8. Have been struggling with this for days.    I've done this many times before with Linux and Windows with other distros. Just can't figure out why the operating system is unable to be accessed. Is there some way to set up a separate bootable Ubuntu partition for 10.4?   Is there something I'm missing. Thanks

---

### Post by jeffpas on 2013-04-16
> **jeffpas said:**
> Hi All,  I have an Ubuntu 10.4 installation boot disk, and all I'm trying to do is set up a partition on a new Windows 8 machine. I've used Gparted and set aside the space (unallocated), then installed Ubuntu but after rebooting, there's no grub loader!  It just boots directly to Windows 8. Have been struggling with this for days.   Just can't figure out why the operating system is unable to be accessed. Is there some way to set up a separate bootable Ubuntu partition for 10.4?   Is there something I'm missing. Thanks  This is the most frustrating thing ever.   Why won't the blinging thing bring up a boot menu, like all the articles say?  I'm ready to dump Ubuntu and go with some other brand of Linux, this shouldn't take two days..........ready to throw in the towel :/ I didn't have any of these problems with Red Hat.

---

### Post by jeffpas on 2013-04-16
can I at least ask... why does the "Try Ubuntu" option off the Ubuntu install disc, not have any internet capability?  All of the solutions on the web for missing grub bootloader talk about selecting the "Try Ubuntu" and then downloading fixes, such as efibootmgr.    Yet when I bring up this option and load the sample operating system, I can't access the internet even though I'm fully wired and connected. No fixes will download, because they can't be accessed.  Every other operating system I've loaded doesn't have any internet setup at all, I just load Firefox for instance with my DSL and off it goes with no setup, it just connects.   This apparently asks for a MAC address and the like(??)   Or does the sample Ubuntu just not have internet.  Its a shame I liked the trial of Ubuntu, I just can't get the thing to load for real which pretty much ends things.  Thanks.

---

### Post by oldfred on 2013-04-16
Is this a new Windows 8 computer with secure boot? 
And you are trying to boot 10.04 which does not even have UEFI support?

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by ubfan1 on 2013-04-17
New machines frequently have new hardware for which the install media does not have drivers.  You need to identify the hardware on your machine
(lspci -vvnn) then locate the (vendor supplied) driver or source and perhaps build it and install it.  If you supply more detail information, more specific help may be offered.  A particular nuisance is the broken persistence on the live media when booting on a secure boot/uefi(?) machine, making moving new packages onto the machine more difficult.

---

### Post by jeffpas on 2013-04-17
Is there any way I can just temporarily force it to load the Ubuntu installation I installed, so I can at least look at it?   I've installed it at least three times now and can't access it on the computer at all.  It just boots directly into Windows 8 with no grub loader option. The only choice I have if I boot off the DVD is the "Try Ubuntu" which will load the sample, but as I said it has no internet.  I managed to install the wireless card driver there but it still says the card is unrecognized (works fine whenever Windows 8 comes up, wireless and wired).   The Help says "Ubuntu should connect automatically to the Internet".   It did not.  :/  I have Secure Boot mode turned off, Quick/Fast Boot turned off.   Apologies, but I am a little unfamiliar with this operating system. Are you saying 10.04 will NOT work with dual boot?  Unfortunately that is the version I have on bootable DVD, not sure how to load a newer one as it won't access the internet even in sample mode. However I have briefly tried the latest version of Ubuntu elsewhere with its icons down the left side and frankly the 10.04 seems much simpler and more straightforward to use for me......I was really pretty impressed by how easy it was to get to things compared to the silly Windows 8 interface.   I really would have no qualms about using the 10.04 if I could just access it  :(

---

### Post by oldfred on 2013-04-17
To many drivers have changed. I run 12.04 with gnome-panel or fallback with is almost the same menu, and panel layout as 10.04. You can also install Xubuntu or and of the other flavors that have different Desktops.

If Windows boots download the new copy of Ubuntu and install to a flash drive. Instructions in link below.
       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick

[/URL]
 gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

---

### Post by fantab on 2013-04-17
Ubuntu 10.04 is quite old and will reach its "end of life" sometime next month, most of the time you will face difficulty in getting it to work with newer hardware. There is no point struggling with it. And by the way, Ubuntu Live CD/USB does have network. Perhaps you need to configure it. But that's for later.

First of all, get yourself a copy of Ubuntu 12.04 or 12.10. You can even get [13.04 beta2]("http://cdimage.ubuntu.com/daily-live/current/"): 13.04 is due for release either at end of this month or very early next month. Its quite stable. 

Secondly, please answer **oldfred's** questions in his post #4, so we know what the setup is. Computers with pre-installed Windows8 have some new features like "**Secure Boot**", which does NOT allow any other OS to boot and **UEFI**, which is a new alternative to older BIOS. To Boot Ubuntu with these features you will need some additional steps before you can install Ubuntu. That is why oldfred asked you those questions. Please carefully read his posts and read the links. 

Once we know what you have we can tell you how to go about it. Also, tell us about your computer's specs. It helps to know.

---

### Post by jeffpas on 2013-04-17
Hi, good ideas, thanks.... well aware of the eternal drumbeat to upgrade everything.... though I've always found upgrades in general more frustrating than anything.   Great new concepts in software always seem to get more and more complicated and topheavy as programmers endlessly tinker with them. Nothing personally against Ubuntu.  Nevertheless, I'm pretty much forced to 12.04... I downloaded off the link and used a remarkably easy tool called UNETbootin, created a bootable USB with 12.04_Live, off of the downloaded iso, ubuntu-12.04.2-desktop-i386.iso.    Unfortunately when I went back to my Windows 8 machine, and booted F12 off startup (and saw the USB and chose it), the OS booted straight into Windows 8 again.   No Ubuntu install menu, nothing.   I've got fastboot turned off, and have all the bios settings I can think of (and Ubuntu 10.04 boots off the DVD-ROM fine with the F-12 option). I suppose the ending couldn't be that easy.   Still trying to figure out how to get it to actually allow me to install 12.04.     Either Windows 8 Gateway is trying to keep Ubuntu out, or Ubuntu doesn't want in......will keep trying, if anyone has seen this happen and knows what to do, thanks for advice :/  Running a Gateway DX 4870-UB17 (brand new) with Windows 8

---

### Post by oldfred on 2013-04-17
Please go back to my first post with links to detailed instructions.
Only the 64 bit version works with UEFI & secure boot systems. And you have to boot in UEFI mode not BIOS mode to be able to dual boot. 
Both UEFI and Ubuntu offer BIOS mode or UEFI mode.

---

### Post by jeffpas on 2013-04-17
Okay I've got it, and it allowed me to install- I think we have a go here.  And UEFI/64 noted, will update.   Thanks guys!

---

### Post by jeffpas on 2013-04-17
Okay first: The 12.04 version is the new, awkward interface with the buttons down the left hand side, and missing close buttons in windows, etc. I really miss that plain, simple easy menu system of v10 :(   Darn!!!  It only existed to taunt me.  Oh well, I'll get used to it.  I burned the 64 bit image to a USB, careful to set the BIOS to non-Legacy or EFI mode which only recognizes the hard drive and the USB.  I created an EFI 'partition' FAT32 200MB per the suggestions in the Ubuntu help. Then I installed 64 bit Ubuntu setting the grub loader to the main disc, with two partitions a swap (2 Gig) and the rest on /.    I DID see the black, non-purple install screen that is supposed to indicate an EFI mode installation.  Unfortunately, after installing, it still went directly to Windows 8 once again, if possible, even faster this time--- though it could be my imagination.  No chance to dual boot or see Ubuntu 12.04, although I can access the web now in the Trial Mode.  What am I missing??   I think maybe the creation of the EFI partition was wrong but it was rather vague.  I'll keep looking....  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jeffpas on 2013-04-17
Got it!!!  You have to run Boot-Repair after the installation, which is loaded while in Try Ubuntu mode, according to this document  [https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)  thanks everyone--- I think its working.    I look forward to using the system.  :)

---

### Post by oldfred on 2013-04-17
Glad you got it working.

You can only have one efi partition per hard drive. All systems put their boot loader into a separate folder in the one efi partition. You can use gparted's set boot flag to define which partition is the efi. And you should not have boot flag on any other partition.

---

### Post by fantab on 2013-04-18
> **jeffpas said:**
> Okay first: The 12.04 version is the new, awkward interface with the buttons down the left hand side, and missing close buttons in windows, etc. I really miss that plain, simple easy menu system of v10 :(   Darn!!!  

If you don't really like Unity [desktop] then you have options: you can install [Gnome-fallback or Gnome-Classic]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed") or you can install [Cinnamon-desktop]("http://www.noobslab.com/2012/10/install-latest-cinnamon-163-in-ubuntu.html") (it is new desktop developed by Linux Mint Team). You don't have to remove anything if you want to try these options. After installing either one or both you can change or choose your desktop from the ubuntu login screen. Try both, and why not.

Glad that you successfully installed Ubuntu.

---

