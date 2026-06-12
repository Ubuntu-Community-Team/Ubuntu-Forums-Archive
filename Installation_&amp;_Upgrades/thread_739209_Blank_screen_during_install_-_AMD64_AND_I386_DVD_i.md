---
title: "Blank screen during install - AMD64 AND I386 DVD installs"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by tstaddon on 2008-03-29
Hi,

Bit of a noob so apologies if I'm getting the terminology wrong.

I have a fairly standard P4 3.2ghz system (intel 915p chipset), with a Radeon X1050 graphics card, 1.5GB of ram and a DVI connector which is as much use as a chocolate fireguard as I have an analogue monitor - so I use TV-out.

In Windows 2000 and XP, DOS, BIOS, the Ubuntu install splash screens AND the console, I have a picture. 

The picture disappears the second I get into the graphical portion of the installer OR the liveCD boot OR the half-finished install on the PC itself. Whether I'm using the I386 dvd or the AMD64 one (both DVD ISOs were checksum OK, and from another machine I have verified the disks' contents).

 have tried EVERY combination of switches and still have been totally unable to get a picture. 

Splash screen OK, console prompt OK, BIOS OK, but no picture when the graphical interface starts. I can hear it playing a jingle but that's it.

I can't use apt-get because I use a wireless adaptor which cannot be configured until further on. Despite that, APT-GET ignores the DVD completely and tries to browse the web for a download. Because it can't connect, it won't install the display package I specified. 

Hello! Why do you think I downloaded the 3.8GB ISO ?! 

On the PC itself I edited the xorg.conf file and all the sections for the display are empty. I'm guessing the graphical installer has, very stupidly, decided to boot into an unsupported mode and THEN ask me what the display settings need to be?!

I'm a linux noob (desktop wise) but not a computer noob. After all these years developing Linux you'd have thought that someone might've noticed that the "blank screen" issue does keep cropping up, and eitehr:

1. tweaked the text-based installer so it'd figure out (or ask) what GFX card you have, then figure out (or ask) which interface you're using as your default monitor, **and only proceed into a graphical boot AFTER the display settings have been confirmed by the person doing the install.**

2. Use a "safest mode possible" graphical install where it doesn't matter what monitor you've got plugged in, OR what interface it's connected to.

---

### Post by Pumalite on 2008-03-29
Have you used the Alternate CD to install? If so; you have to go though with the installation and configure your Xserver at the end (at the blank screen. That's not Ubuntu's fault, but ATI, that up to now has refused to support Linux). BTW, I advise you to be wired to the Internet during install. Configure your wireless later.

---

### Post by tstaddon on 2008-03-29
Hi,

I have tried it with the AMD64 alternate installs, and the I386 alternate install, both Gutsy and Hardy. No joy.

I can complete the text portion of the install OK, the machine reboots OK, I get the GRUB menu OK, I get the splash screen / scrolling debug text OK - but as soon as the DE starts up... 

NOTHING. Nada. Zip.

I did - once - manage to get a desktop with a Gutsy I386 livecd, but the install conked out halfway through and it appeared to be a corrupt disk because it would hang consistently at 83% even when I used a different CDROM drive and installed to a different PC altogether. 

Wierdly, I downloaded the ISO again and burnt it again - and that disk verifies OK, but the system starts up blank post-install. With the AMD64 disk I don't get a picture at all.

I tried the alternate CDs, and eventually the DVDs.

I appreciate what you're saying about ATI, but surely it's not too much to ask, for a modern O/S release to at least offer a generic SuperVGA driver during the install routiine (that'll work with a stock Nvidia/Radeon card)?

---

### Post by Pumalite on 2008-03-29
That driver you are talking about is 'vesa'. Never fails. Let's start with you telling us what your hardware is in detail.

---

### Post by tstaddon on 2008-03-29
Graphics card: Radeon X1050 PCI Express half height card - no VGA connector, just DVI and Tv-Out.

Motherboard: MS-7046 Rev 1, Philips BIOS release.

CPU: Intel Pentium 4 550 (EM64T support)

TV tuner card - Twinhan DVB-T PCI (BT878).

2 standard IDE hard disks (Seagate 30GB for system, Maxtor 200GB for data).

1 generic DVD drive in an external USB cage (which mounts fine).

The reason I can't use the wired connection is because

(a) this PC is located three storeys away from the router and I physically don't have a cable long enough to reach

(b) the PC can't be hosted in the front room within reach of the router

Also, my broadband is 320kbits if I'm lucky (I live out in the country, several miles from an exchange) and has a usage cap so any solution that requires me to have alays-on internet access and doesn't do everything from CD is going to be a grade one pain in the a**.

---

### Post by Pumalite on 2008-03-29
I think you have to start trying some boot parameters. Here some guides on how to do it and collections of them:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

Use the most common first (alone or in different combinations):
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

To be sure, try your CD's in different computers and clean the lens in your burner.

---

### Post by tstaddon on 2008-03-30
Hi,

Well, I was up till 3am trying out various combinations of switches and got nowhere - but I tried the liveCD again, used F to set it to start in safe display mode and it came up. I was then able to install using the stock VESA driver. The ATI driver is on there but not enabled.

I don't know why this worked to be frank - Ive tried the same thing with the same disk before (and in fact with the I386 disk AND the AMD64 DVD) and no matter what i did, it would still enable the ATI driver. 

So, I'm pretty sure the issue is the graphics driver being imposed on me through the text-based install or within the graphical install. 

If the liveCD physically booted up with the VESA driver, or the user is doing a command-line install, that's the VESA driver should be used by ANY installer unless a different driver is specifically requested.

To be brutally honest I don't think autodetecting graphics cards during a text-based install is EVER a sensible thing to do unless you FULLY support the driver, RELIABLY detect which card is being used, and any variables in the equation which would induce a user to oveerride the defaults (eg you're building a media centre which is connected to a standard analogue TV and need to force your screen resolution to 720x576x16 at a low refresh rate) can be reconciled before the installer completes. 

Going back a couple of years, a Windows text-based install used to ask you which graphics driver you wanted to use and would give you a list of drivers it thought were appropriate. If you can't see your desktop with the drivers you picked, a Safe Mode option will boot the OS with a stock VGA/SVGA driver.

TBH that's the best answer - use autodetect to filter the available driver list to drivers that might be relevant to the card; recommend TWO drivers (one for compatibility and one for optimal performance); and have the user manually select which one to use.

Perhaps provide an "advanced" option allowiing monitor / output selection, alternate driver (for safe mode) and so on.

---

### Post by Pumalite on 2008-03-30
Glad you got it working.

---

### Post by tstaddon on 2008-04-01
I do have it working, after a fashion - in display settings I have two cards listed. the first is using the ATI Rage driver for some reason (and no matter what I do, it stays like that) while the second is the VESA driver (which again it won't let me change). 

Fortunately the second one, not the firrst, appears to be the one that produces the display.

So it kind-a works, but I'm stuck with a choice between 640x480 and 800x600 at a fixed refresh rate because the darned thing will NOT accept any changes - I even installed the Radeon drivers and enabled them on both adaptors, rebooted and zip - back to the ATI Rage driver and VESA driver on the respective adaptors.

So excuse me if there are any typos here; it's because I can't read the text on the screen.

---

