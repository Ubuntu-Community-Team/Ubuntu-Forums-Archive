---
title: "Gigabyte 797 (posibly UEFI) boot/install issue"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by krahvaal on 2014-12-29
Hello,

I have a Gigabyte 797x-sli motherboard that I don't know how to boot Ubuntu 14.04 (any linux with UEFI) on.
SSD has Windows 8.1 although I have tried disconnecting it to boot from DVD.

When using Ubuntu 14.04 DVD...
* normal boot goes to Ubuntu load menu.
* break to BIOS reveals UEFI - ordering as UEFI, DVD (Ubuntu), Windows...straps GRUB.
...each go through lots of DVD chatter then nothing but flashing cursor top left of screen

I've read that I need to set up an Admin password.
The board has User as well as Admin so I'm not going to do anything without proper instruction.

All help greatly appreciated.

Regards,
Greg

---

### Post by grahammechanical on 2014-12-29
There is something I am not clear about. Is Ubuntu installed? If Ubuntu is installed then why are you talking about the DVD? If Ubuntu is not installed and you are trying to run the Ubuntu DVD as a live session, then you do not need a Admin password.

When we install Ubuntu we are asked to give a user name and a password. Doing that will set us up as both a standard user and an administrator. We will do our normal work as a standard user. Then if we try to do anything that only an administrator can do we will be asked to authenticate the action. We then put in our password and for that action we become an administrator and then we go back to being a standard user. Other users will not be able to authenticate actions unless we have set them up as an administrator. This is how we do things in Ubuntu.

Please, clarify whether or not Ubuntu is installed. And if you followed the advice give here,

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]


Regards.

---

### Post by oldfred on 2014-12-29
Not sure if your model has the same issues, but IOMMU seems to be in most Gigabyte boards.

 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by krahvaal on 2014-12-29
As per subject line this is a boot/install issue.

No Unix/Linux installation media will even start up the machine.
It goes through grub/vmlinuz boot/whatever, lots of DVD chatter (as I said) but nothing.
This is regardless of disabling fast boot etc.

From what I have read I need to set up a BIOS account with PASSWORD.
The Gigabyte 797x-sli motherboard BIOS has both ADMIN and USER accounts each requesting a PASSWORD.
From what I have read, it would appear that non windows distros won't pass muster with out them.
Is this correct?
Which/both do I enter so as to get things going without screwing up whatever?

---

### Post by oldfred on 2014-12-29
The 97 series are very similar to 87 series. So some of these issues may apply.

 Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure 
[http://ubuntuforums.org/showthread.php?t=2194155](http://ubuntuforums.org/showthread.php?t=2194155)

---

### Post by krahvaal on 2014-12-29
Thanks for all the rapid response and support, it was quite informative.
While I have not tried other distros I am unable to get any UEFI/Secure Boot Support versions of Ubuntu (12.04.2+) to load a Live DVD (each dvd tested on 3 other machines).
The motherboard has dual UEFI Bios where I can set everything to legacy with no change to the problem.
I have tried quite a variety of settings to no avail.

Whether it uses the grub or ubuntu loader the result is as follows...
* Menu - chose try.
* Black screen with flashing cursor at top left with varied DVD activity.
* 2-3 minutes DVD halts leaving black screen with flashing cursor and no response to keyboard.
...
I've just tried ubuntu-9.04-desktop-amd64.iso and it boots the Live DVD.
I will now try installing it to a drive then update it to see what happens.

---

### Post by krahvaal on 2014-12-30
After numerous attempts and shuffling around a terrabyte of data I give up.
The ubuntu-9.04-desktop-amd64.iso installer gets to the end with a fatal error on trying to create the loader.

---

### Post by oldfred on 2014-12-30
Your hardware is so new, that the 9.04 does not have a chance to work with it and it is obsolete anyway. Even early versions of 12.04 would not as Intel made many improvements were added to kernel, support software and video drivers. 
With the very new chip you have you need at least 14.04 and perhaps 14.10 or even the daily update of 15.04 that is still about only at beta and may not be always reliable as they keep adding things.

---

### Post by krahvaal on 2014-12-31
Thanks olfred, 9.04 was a long shot but it seemed to be running off generics and I hoped to upgrade if it installed.
While it installed, I couldn't get 9.04 live to network let alone write to the mbr. None of my tools would load/swap into the new kernel.

I apologize for misleading everybody but in my ignorance I have been confused about the problem(s).
EFI seems to have little if anything to do with this and there appears to be a graphics problem - I don't know if it's chipset or card.

One distro (soz I forget) failed straight after it's boot menu with the message "Unknown chipset".

Fedora 21.5 loaded the live usb but only in "low graphics" mode. While at it I installed fedora to check for whatever other issues.
I had to manually partition to stop it screwing up the data partitions.
I had disconnected the windows ssd and another data hdd so had to create an EFI partition as well as mount it in advance for the installer to validate.
When I reconnected my other drives fedora grub failed until I ordered disks/partitions precisely in bios.
After a number of tests I am satisfied that ubuntu should work on the machine and was quite ready to get rid of fedora.
Even after I hosed the extended partition that I used for fedora bios still shows the fedora EFI even despite disconnecting the associated drive.
Anyone know how I can remove it from bios without taking out windows 8's efi while at it?

Back to ubuntu.
When I removed "quiet splash" from 14.04 live boot I saw it was failing just after a video ram statement.
I then tried to load in low graphics mode by adding vga=771 etc for 8, 16 and 24 bit across 800x600 and 1024x768 all with the same outcome...

[ 3.231643 ata1: SATA max UDMA/133 abar m2048@0xf7839000 port 0xf7839200 irq 46
[ 3.231644 ata2: DUMMY
[ 3.231645 ata3: SATA max UDMA/133 abar m2048@0xf7839000 port 0xf7839200 irq 46
[ 3.231645 ata4: DUMMY
[ 3.231646 ata5: DUMMY
[ 3.231646 ata6: DUMMY
[ 3.231676 i915 0000:00:02.0: enabling device (0006 -> 0007)
[ 3.265646] usb 1-1: new high-speed USB device number 2 using ehci-pci
[ 3.273099] [drm] Memory usable by graphics device = 2048M
[ 3.273115] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[ 3.278948] MXM: GUID detected in BIOS
[ 3.281889] fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver.

...on DVD it spins up for about 10 seconds, chatters for around a minute or so then silence with a white flashing cursor, no I/O - usb much the same just gets there in a err...flash ;).

NOTE: as mentioned, older distros/versions are loading to live DE on generics but of no use for upgrade to current.

This is what I know about the hardware...
Gigabyte Z97X-SLI...
...Intel GbE LAN with CFOS internet accelerator software
...Realtek ALC1150 115dB SNR HD Audio with built-in rear audio amplifier
...GIGABYTE UEFI DualBIOS
Intel(R) Core(TM) i7-4790S CPU @ 3.20GHz (8 CPUs), ~3.2GHz
16384MB RAM
NVIDIA GeForce GTX 970 4096 MB GDDDR5

Whatever I've searched on "Ubuntu with NVIDIA GTX 970" relates to updates and/or driver issues which does not help with getting the live media running on my machine.
Whatever I've searched on low graphics mode is about overcoming, not commanding it.

Are there commands I can use to force the live media to boot on vga and/or whatever generics required, long enough to install Ubuntu 14.04.
Are there tools that can provide more information such as potential hardware conflicts?
Is it possible Ubuntu 14.10 Live will load and/or install?
While I'd much rather LTS I'll go with whatever works.

Thanks once again for the help here.

---

### Post by krahvaal on 2014-12-31
Much the same problem with Ubuntu 14.10

---

### Post by oldfred on 2014-12-31
That nVidia card is extremely new and I have seen where they have to use a ppa to load the very newest drivers to have it work.
Can you boot with the built in Intel chip?  If so you may still need settings in boot stanza.
Does nomodeset work? If Intel see other options in by in ubfan1's post below.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

nVidia driver tests:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1)
> The GeForce GTX 970/980 new Maxwell GPUs also couldn't be tested since  there isn't any hardware acceleration support with Nouveau and that's  currently blocked by NVIDIA providing their new signed firmware images. 

---

### Post by krahvaal on 2015-01-01
Thank you once again olfred.

After a bit of trial and error I was able to get all [OK] messages but still black screen.
Searching on the commands I came across Mint, black screen and nomodeset. It advised adding grub_gfxmode=1280x1024x24 if needed which worked for Mint but not Ubuntu.
All variations I have tried still with 14.04 live still end up at black screen. It seems determined to fall back to nouveau which I almost sure can not run my setup.
I tried modeset=0, nouveau.modeset=0, others and combinations with no success.
Variations of the other boot options on those links don't seem to make any relevant difference.
Of course, I am doing a lot of guess work which is rapidly going nowhere.

Mint installed but was a pain forcing it to load into "software rendering mode" as editing grub to do this failed.
Getting the latest proprietary nvidia driver to install was a bit of a nuisance but I got there in the end.
After re-connecting the other drives it was just a case of running update-grub2 for it to resolve EFI partitions for dual boot.

Being Debian I'll keep using it to expose any issues that could relate to Ubuntu.
IF anyone can tell me how to force "software mode", vga, whatever to load 14.04 live DE I'd rather get on and install it instead though.

Regards,
Greg

---

### Post by krahvaal on 2015-01-02
The UEFI issue was my mistake so I am signing this off as solved.
The live 14.04 media is insisting to fall back to nouveau at startx/whatever and therefore blackscreen on my GTX 970.
Having scoured the internet and tried things over a couple of days with no solution I will start a new thread for that.

---

