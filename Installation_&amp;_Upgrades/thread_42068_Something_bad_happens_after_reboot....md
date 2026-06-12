---
title: "Something bad happens after reboot..."
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by celloandy on 2005-06-15
I've been using Ubuntu for several months (converted from Gentoo), and have successfully installed it on both my desktop machine and my laptop.  This weekend, however, I was trying to do an install on a friend's PC, and have been having issues.  All three times that I've tried, I got through the whole initial install just fine, popped the CD out, and rebooted, and it booted just fine, and started installing packages.  All three times, it got (what I think was) most of the packages installed, then spontaneously went crazy and started flooding the screen with crap like:

[<c0116444>] release_console_sem+0x85/0xb9

This message was chosen randomly from the pages and pages it spewed.  On the first and third attempts, it went for a bit and then stopped, and was non-responsive.  On the second time, it just kept spitting out messages until I turned it off.  All three attempts died in roughly the same spot, just a bit after the message about setting up the Mozilla Firefox chrome (it's tough to see exactly which package it was installing when it failed, as the screen quickly becomes obscured with error messages).  I thought initially that it just might be a bad spot on the hard drive, but each attempt used a slightly different partition scheme or filesystem format (tried different sizes of partitions, and ext3 as well as reiserfs filesystems), so it seems like that would make it at least die in a different place each time.  He's told me that if I can't make it work, he's going to install Red Hat (ugh!), so any help is greatly appreciated.

Andrew

---

### Post by desdinova on 2005-06-15
erhaps disable ACPI in the bios and try again?

---

### Post by celloandy on 2005-06-17
Do you think I'll want to disable it in bios, or with kernel parameters (e.g. acpi=off) through grub?  Also, is there any reason you think acpi is causing the problem, or is this just sort of generic fix-all for common problems?  (Sorry if that sounded rude.  I didn't intend it that way... it's just that each install attempt takes some time, so I want to make sure I've got something good to try for the next time around.)

Andrew

---

### Post by codejunkie on 2005-06-17
try the live cd on this computer if it loads up fine, it should install just fine and with the live cd you can test the acpi issue if it fails to load the live cd then try live acpi=off if that fixes it, it is an acpi issue, so add linux acpi=off to grub and it should work this might save you from reinstalling several times to fix the problem. i've also noticed if you have more than one video card in the computer at the same time ubuntu seems to freak out during install if the motherboard has onboard video and another video card installed make sure onboard video is disabled in the bios.

---

### Post by celloandy on 2005-06-17
Alright, I'll give this stuff a go.  The weird thing, though, is that the actual install process (partitioning, installing base system, etc.) works fine.  Even after the reboot without the CD, it works just fine and installs packages and everything just fine for about 20 minutes or so, and *then* it dies, in about the same spot in the install every time... whatever the problem is, I'm not sure that it'll be exposed by just booting the livecd, but I'll try it.

Thanks,
Andrew

---

### Post by celloandy on 2005-06-21
Tried loading the livecd.  I didn't specify any kernel parameters, at all, and it booted fine.  dmesg shows ACPI is performing as it should.  At this point, I might try to reinstall without ACPI, but I see nothing to support the hypothesis that this is what is causing the problem.  Does anyone know why this was recommended to me?

Andrew

---

### Post by codejunkie on 2005-06-22
[QUOTE=celloandy]Tried loading the livecd.  I didn't specify any kernel parameters, at all, and it booted fine.  dmesg shows ACPI is performing as it should.  At this point, I might try to reinstall without ACPI, but I see nothing to support the hypothesis that this is what is causing the problem.  Does anyone know why this was recommended to me?

Andrew[/QUOTE]

because acpi issues seems to affect alot of newer computers that are designed specifically for windows and using linux acpi=off fixes it by turning off acpi on the motherboard. the reason i mentioned the live cd is you were asking for a way to test without reinstalling over and over and this seems to be the easiest way to test compatibility issues and try different boot methods without reinstalling the os each time.
--------------------------------------------------------------------------------------------------------
usually when it's an acpi issue as soon as you hit enter to install the computer will restart or freeze up, but in some cases it can do just as you described in your first post. this usually happens when it first starts the install but can also happen during the install.

[QUOTE=celloandy]I've been using Ubuntu for several months (converted from Gentoo), and have successfully installed it on both my desktop machine and my laptop.  This weekend, however, I was trying to do an install on a friend's PC, and have been having issues.  All three times that I've tried, I got through the whole initial install just fine, popped the CD out, and rebooted, and it booted just fine, and started installing packages. [COLOR=Red] All three times, it got (what I think was) most of the packages installed, then spontaneously went crazy and started flooding the screen with crap like:

[<c0116444>] release_console_sem+0x85/0xb9

This message was chosen randomly from the pages and pages it spewed.  On the first and third attempts, it went for a bit and then stopped, and was non-responsive.  On the second time, it just kept spitting out messages until I turned it off[/COLOR].  All three attempts died in roughly the same spot, just a bit after the message about setting up the Mozilla Firefox chrome (it's tough to see exactly which package it was installing when it failed, as the screen quickly becomes obscured with error messages).  I thought initially that it just might be a bad spot on the hard drive, but each attempt used a slightly different partition scheme or filesystem format (tried different sizes of partitions, and ext3 as well as reiserfs filesystems), so it seems like that would make it at least die in a different place each time.  He's told me that if I can't make it work, he's going to install Red Hat (ugh!), so any help is greatly appreciated.

Andrew[/QUOTE]

the reason this was recommended to you is to give you some troubleshooting steps  to look at because it can cause the issues you described in your post but it's not the only thing that can. 

heres a couple more things you could try that can cause what you described.
--------------------------------------------------------------------------------------------------------
make sure that if the motherboard has onboard video on it, and an addon video card is installed disable the onboard video in the bios because this will cause errors like you described in your first thread when using the install disk because it trys  to use both videocards at the same time. 
--------------------------------------------------------------------------------------------------------
it could also be a bad disc image that your using to install from download and burn a new install cd and reinstall from that.
--------------------------------------------------------------------------------------------------------
do a server install if it finishes successfully it will bring you to a terminal it will not install a gui interface by default so type sudo apt-get update sudo apt-get install ubuntu-desktop this will download and install up-to-date packages incase an older version of something has a conflict with that system.

---

### Post by mingus on 2005-06-22
The common diagnostic technique to use when the cause is not obvious, is to use kernel arguments to turn off all but essential hardware detection and setup.  Power management is one of the worst offenders, esp on laptops (hence acpi=off).  There can be conflicts with the BIOS irq assignment or the PCI bus, and there are several arguments for this (such as noapic).  Video is common, sometimes because its memory mapping is wrong (so turn off framebuffer).  Etc.

Not fun, but usually it eventually gets you to the source of the problem.

---

