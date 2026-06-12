---
title: "Installing Ubuntu on Asus N550LF as dual boot with W8... or at all"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by pehoulihan on 2014-04-03
EDIT: It turned out to be some strange issue with the USB key. If anyone else is encountering this I'd recommend using Universal USB Installer instead of Unetbootin to burn the .iso, then, after install, use Boot Repair to get the boot options right and ensure Launch CSM is disabled in Aptio.

Hi, I've been trying to install Ubuntu on my Asus laptop but it's proving extremely difficult to get the bootloader to recognise my liveUSB due to this godawful UEFI thing.

Bit of background: When I bought my laptop I also bought an SSHD and a caddy. My friend very kindly installed the SSHD in the optical drive for me and installed Arch on it. Unfortunately, something went horribly wrong during the install process, and when I tried to get it up and running with a desktop and all the other usual bits and pieces I found that all the libraries needed for internet access and... most other things weren't to be found. Installing them from USB did nothing so after a few weeks of booting back and forth between W8 (to search for and write down terminal code) and Arch (to try typing in said code in the hope something would happen) I gave up and decided to just try installing a distro which has all the required libraries as standard.

Fortunately, my friend had taken care of most of the donkey's work like disabling fast boot in W8 and disabling secure boot in aptio, so I can at least access the boot menu easily enough. I tried first with a UbuntuGNOME 13.10 image. I burned it to the USB with UNetBootin and it all seemed to go OK. It didn't show up as an option on the boot menu so, as per advice on the internet, I enabled Launch CSM. That solved the problem in that the USB key (or something) now shows up as "Generic Storage Device" on the boot menu but when I try to boot from it it gives me an error [I]"[FONT=arial][SIZE=2]Reboot and select proper boot device or insert boot media in selected boot device and press any key[/SIZE][/FONT]."

[/I]I tried adding a boot option, but the only drive it'll let me select to do so is the SSHD Arch is installed on. I also tried using WUBI just on the off chance, but it only recognises the drive W8 is installed on... I don't particularly want to overwrite W8, and the whole point is to install it to the SSHD anyway. I tried burning a generic Ubuntu 13.10 image and used that... but exactly the same problem. I'm pretty sure the USB key isn't the issue as I've used it for a bunch of stuff, it was also the installation media for Arch, which went fine apart from not having some libraries.

So yeah... I'm a bit out of options here. My goal is to set up a dual boot between W8 and UbuntuGNOME, which I'm pretty sure I can do, but not unless I can get the bootloader to recognise the liveUSB. The whole thing is a bit worrying because I used to have no problem installing a new distro using BIOS, but with this whole UEFI thing it's turning into a bit of a nightmare. I'm pretty sure anyone not used to mucking around with their computer like this would have given up long before now.

---

### Post by pehoulihan on 2014-04-03
Hmm, would I have been better off posting this in absolute beginners? I've used and installed Linux distros before, but this kind of stuff is getting a little beyond me.

---

### Post by oldfred on 2014-04-03
Please do not bump but once per 24 hours. Many of us are not on 24 hours a day or even every day, so your thread may not be immediately noticed. We all are voluteers, just trying to help others.

You cannot install wubi in gpt partitioned drives which all new UEFI systems are. That is the main reason wubi is being discontinued.

You must have 64 bit version of Ubuntu or whichever flavor you want to boot in UEFI mode. If Windows is UEFI, you want Ubuntu in UEFI mode. And how you boot install media is how it installs, so you want to boot Ubuntu installer DVD or flash drive in UEFI mode.

Some systems will not boot from caddy in DVD slot. Does yours actually boot from that or was system configured with Arch boot on internal drive and rest of system on caddy drive?

Not familar with Gnome version, but underlying Ubuntu is the same.

What model CPU? Some systems with new 4th Gen Haswell Intel chips need all the updates that Intel had offered to kernel, support software, and video drivers. And those updates to kernel etc with Ubuntu will be in 14.04, but it is still in beta. 

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

More info with many good links for various versions of systems in link in my signature.

Looks like you have Haswell and dual video which also adds a bit to installing. The newest nVidia may work with dual video now, not sure. 
 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

---

### Post by pehoulihan on 2014-04-03
Hi,

Sorry about that, but it was a genuine question, is this in the right forum? I don't expect an answer immediately or anything, I know this isn't a paid tech support service :) Thanks for taking the time.

I was using 64bit images, and I'm trying to install Ubuntu to the SSHD, not the USB key (I'm just using that as install media). The process I've always used in the past for that is: Burn image to disk/usb, boot from the disk/usb and use the menu to install to a hard drive. It always worked fine in the past with BIOS, but maybe I'm wasting my time trying it with UEFI?

That's a good question, I didn't do the Arch install myself so I'm actually not sure, all I know is that Arch seems to boot up fine and it's an option in the bootloader. The regular HDD is slot number 0 and the SSDH is slot number 1. When I tried to set up new boot options the only path it would let me choose seemed to point to slot 1 so I think it's booting off that disk, but I'm not sure.

I'm not too worried about installing UbuntuGNOME itself: If I can get regular Ubuntu installed I can always install Gnome afterwards. What's bothering me is that I can't even get the liveUSB recognised.

Specs are as follows...
* Processor: Intel  Core&#8482; i7  4500U  Processor
* Memory: DDR3L  MHz SDRAM, 2x SO-DIMM socket, SO-DIMM Up to 16 G
* GPU: NVIDIA GeForce GT 745M  with 2GB/4GB DDR3  VRAM

Hmmm, so I might have to wait for the next LTS? Another few weeks won't hurt I guess. If I survived W8 this long I can wait a little longer :)

Thanks for the links, I'd already tried to follow the first one, but I can't get the liveUSB to boot at all. I'll give the rest a look though. Thanks again for taking the time to respond.

---

### Post by oldfred on 2014-04-03
Some UEFI/BIOS require added settings to let you boot from USB ports. Not only do you have to make sure secure boot is off, but also enable USB ports for booting. Check USB settings.

You should see two boot options for flash drive, one UEFI and one not UEFI but often not clear what it is, may be BIOS/CSM/Legacy or just label of flash drive without UEFI.

I just installed 14.04 in a test partition, but my system is BIOS only.

If you want to know details of existing system run the BootInfo report. Not sure if it runs ok from Arch, but you can run from Ubuntu live installer once you get that going. May be best to know, so we can make better suggestions on overinstalling with Ubuntu.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

A thread on Dell's said you have to have legacy boot on even when booting in UEFI mode as Intel has some internal issue in its software.

---

### Post by pehoulihan on 2014-04-03
Hi,

That's all very helpful thanks. I'll try looking through the USB settings to see if I missed anything, would you recommend trying the 14.04 Beta rather than 13.10?

I'll have a go at bootinfo too and see what comes up. Would I need to use bootrepair just to get things going? Or only if things go wrong? Thanks for the link at any rate. Wow, that bootmenu looks much fancier than mine :)

---

### Post by oldfred on 2014-04-03
You may have better luck with 14.04. Just realize it is beta, but it just hit feature freeze and only last minute bugs will be worked on until final release. As long as you do not have it as the only way to boot, you an install it. Several others (not sure of models) with new Haswell based systems found it worked better. But some other systems also worked better with older installs like 12.04 before the current 12.04.4.

Most of the fixes now in newest Ubuntu, now do not require Boot-Repair to fix up anything. Only those systems with 'buggy' UEFI or those where vendor modified UEFI to only boot Windows may need work arounds.
But Boot-Repair is also a very good tool to document and understand details of system. 
Run it and post link to BootInfo report.

ubfan1 just posted in another thread that some also require you to set an adminstrative password in UEFI to get things to work. I have seen that before but forgotten. Not sure which models.

---

### Post by pehoulihan on 2014-04-03
Thanks, I'll try all that so. Setting an admin password shouldn't be too much trouble, I know where it keeps that.

---

### Post by pehoulihan on 2014-04-04
Right, I had a go at the following:

-Tried burning a 14.04 image, just in case it all magically decided to work, sadly it didn't XD

-I set an admin password in the Aptio menu just in case it unlocked any hidden security features, no such luck

-Had a hunt through the settings in case there was anything about USB, there was, but it's all enabled anyway. Handy though: If I ever need to freeze my USB ports from startup I now know how :D

-I asked my friend about the Arch boot option, he says it points to the main HDD as you suggested, then wanders off to the SHDD from there

-Couldn't find any information on bootinfo, but I'll give it a go anyhow

Overall: Wow, wintel have really done a number on linux/everything else here.

---

### Post by oldfred on 2014-04-04
If you can still boot into Arch, you can download this. It runs mostly standard Linux commands, not sure if Arch has them all or not. Then just run the BootInfo report.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by pehoulihan on 2014-04-05
I suspect that won't work for me: The main trouble I've been having with arch is trying to get internet access. Some of the necessary libraries seem to be missing, and pacman doesn't seem to be willing to install from USB. The liveCD is a no-go for the same reason that I can't get the Ubuntu live image going.

I had a hunt around in the /bin folder in arch on the off chance that bootinfo was already installed. It wasn't, but I did happen to find a promising looking utility called bootctl. I ran it and it outputted the following:

/bin #: bootctl

System:
    Machine ID: (Long alphanumeric string, let me know if this is important and I'll type it out) 
    Boot ID: (Long alphanumeric string, let me know if this is important and I'll type it out)
    Firmware: UEFI 2.31 (American Megatrends 4.654)
    Secure Boot: Disabled
    Setup Mode: Setup

Selected Firmware Entry:
    Title: Linux Boot Manager
    Partition: /dev/disk/by-partuuid/75f1eda7-17aa-485d-9676-45bl2be4592f
    File: ¬/EFI/gummiboot/gummiboot-x64.efi

Boot Loader:
    Product: Gummiboot 43
    Partition: /dev/disk/by-partuuid/75f1eda7-17aa-485d-9676-45bl2be4592f
    File: ¬/EFI/gummiboot/gummiboot-x64.efi

Is any of that useful?

---

### Post by oldfred on 2014-04-05
Helps a bit as you have Arch in UEFI boot mode with secure boot off. And are using gummi boot which is another UEFI boot manager which I know nothing about.

Some systems just seem to get locked up. Full cold boot then may work. If laptop remove battery also. And hold power switch down with battery out, to drain residual power to make sure it gets totally reset.

Are you correctly installing Ubuntu to flash drive?
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by pehoulihan on 2014-04-05
"And are using gummi boot which is another UEFI boot manager which I know nothing about."

Well that makes two of us ;)

"Some systems just seem to get locked up. Full cold boot then may work.  If laptop remove battery also. And hold power switch down with battery  out, to drain residual power to make sure it gets totally reset."

I've seen some suggestions for that before, will that reset everything to factory settings? If so, will my arch boot still exist? Not that it's much use now, but I doubt I'd be able to get it back without help.

I've been using unetbootin to burn the images to my flash drive, it's the one I've seen recommended most on various different tutorials. I'll try the one Ubuntu recommends though (UUI), maybe it'll work better.

---

### Post by pehoulihan on 2014-04-05
I think I just had an epiphany: Both boot options in Aptio are pointing to the same partition on my HDD, just to different .efi files. Arch's one must tell it to do everything else off the SHDD. Maybe I just need to copy the Ubuntu .efi across to that partition, edit it to refer back to the USB stick, then point a new boot option in that direction?

It's either a solution or I'd break everything, not sure which.

---

### Post by oldfred on 2014-04-05
After an install, I have seen users move efi files around. 

 Users who manually moved efi files around:
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
      
 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

What I do not fully understand is how an efi boot knows where to go. And some installs with RAID or LVM have had issues and just added another grub.cfg in efi folder. One user posted this:


 configfile (hd0,gpt8)/boot/grub/grub.cfg

 found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

Any efi partition on any drive, should be able to re-direct to other installs and boot those.

---

### Post by pehoulihan on 2014-04-06
Good news,

So I tried Universal USB Installer and it gave me a very interesting warning: "USB Device Will not be bootable." I thought that sounded a little suspicious so I decided to try another USB key and, lo and behold, it booted. I've no idea what the problem was with the first one, since it seems to work just fine for everything else, but for some reason it won't boot live images. If anyone else is reading this, Unetbootin won't give you this warning message, UUI will.

I installed UbuntuGNOME to my SSHD, it all appeared to go smoothly. When I restarted there was no boot option for it in UEFI so I ran Boot Repair as you suggested. This added a Ubuntu option to the bootloader, but it doesn't really work for some reason. The windows option now loads grub however so no problems there. I did find that the windows option would only boot properly if I interrupted the boot process, went into settings and booted it from there, for some reason it would encounter a "no such device" error if it tried to boot the option directly. I was able to solve this by disabling Launch CSM again.

Thank you so much for your kind help, even though it turned out to be a trivial problem I never would have worked it out without your advice, and the problems I encountered afterwards were solvable given your suggestions.

---

### Post by oldfred on 2014-04-07
Glad you resolved it.

Just to document how install is you may want to run BootInfo report.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you have no issues, you do not need to post it, just have they documentation on how it is installed. 
I run the part of Boot-Repair - bootinfoscript that is just a bash script to document my system as part of my rsync script backup, so I have most current info in backup.

---

### Post by pehoulihan on 2014-04-07
Thanks, I'll do that.

---

