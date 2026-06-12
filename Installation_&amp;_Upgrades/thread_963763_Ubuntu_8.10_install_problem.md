---
title: "Ubuntu 8.10 install problem"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by integracd on 2008-10-30
Hi,

:confused::confused::confused::confused::mad::mad::mad:
I am trying to install Ubuntu 8.10 64bit and when boot from the CD I am having a weird problem.  The CD boots up fine into the startup menu asking me what I want to do.  I can choose to either Try ubuntu, install ubuntu, check memory or boot to the first local HD.  If I select all but the boot to first HD nothing happens.  Boot to first HD is the only option that works and it does not matter how many times I press enter on the install ubuntu or try ubuntu.  After I press enter and try to select something I can still move the cursor up and down and try to select something else.  Anyone have any ideas as to what might be happening?

I have also tried burning a different CD, using a different computer, and even redownloaded the ISO from a different source.  But nothing seems to work.  Any help would be greatly appreciated.

Thanks in advance.

---

### Post by EnGorDiaz on 2008-10-30
> **integracd said:**
> Hi,

:confused::confused::confused::confused::mad::mad::mad:
I am trying to install Ubuntu 8.10 64bit and when boot from the CD I am having a weird problem.  The CD boots up fine into the startup menu asking me what I want to do.  I can choose to either Try ubuntu, install ubuntu, check memory or boot to the first local HD.  If I select all but the boot to first HD nothing happens.  Boot to first HD is the only option that works and it does not matter how many times I press enter on the install ubuntu or try ubuntu.  After I press enter and try to select something I can still move the cursor up and down and try to select something else.  Anyone have any ideas as to what might be happening?

I have also tried burning a different CD, using a different computer, and even redownloaded the ISO from a different source.  But nothing seems to work.  Any help would be greatly appreciated.

Thanks in advance.

whats ur comp specs?

---

### Post by integracd on 2008-10-30
Core 2 duo E6600 CPU, 2 GB DDR2 Ram, Dell Optiplex 745 with two 260GB SATA drives., Nvidia EGeForce 8600 GTS

---

### Post by ehorton on 2008-10-30
I am having identical issues.  I have tried different burn speeds and three different computers.  All have similar symptoms.  I have a Dell XPS M1330 with 4gb Core 2 Duo processor.  8.1 beta is currently on here and it worked/installed fine.  So if someone has found a solution I would appreciate the feedback and I know integracd would too.

---

### Post by rockstar82 on 2008-10-30
I had similar problems. My computer rebooted itself just as i pick an option. Disabling an EHCI-option in bios solved the problem. Asus P5B-VM motherboard.

---

### Post by dave on 2008-10-30
I have the exact same problem.  I don't even get the "loading kernel" popup.  I played around with the different modes of the CD to no avail.

I'm running on a Core2Duo Dell.  With 4GB ram.

I've hit escape to go to the command-line boot, does not help.  Hitting just plain enter at the command-line boot brings up another GUI based loader, that just hangs as well.

Would be nice to know how to fix.

--
Dave

---

### Post by Mason Whitaker on 2008-10-30
My disc booted on a Virtual Box fine on my Mac, I just need to wait untill I get home so I can actually boot it.

---

### Post by bishboria on 2008-10-30
> **integracd said:**
> Hi,

:confused::confused::confused::confused::mad::mad::mad:
I am trying to install Ubuntu 8.10 64bit and when boot from the CD I am having a weird problem.  The CD boots up fine into the startup menu asking me what I want to do.  I can choose to either Try ubuntu, install ubuntu, check memory or boot to the first local HD.  If I select all but the boot to first HD nothing happens.  Boot to first HD is the only option that works and it does not matter how many times I press enter on the install ubuntu or try ubuntu.  After I press enter and try to select something I can still move the cursor up and down and try to select something else.  Anyone have any ideas as to what might be happening?

I have also tried burning a different CD, using a different computer, and even redownloaded the ISO from a different source.  But nothing seems to work.  Any help would be greatly appreciated.

Thanks in advance.

I'm having identical problems.

After a while the ubuntu logo and progress bar disappear and displays buffer I/O error on device sr0...

---

### Post by rampras on 2008-10-30
Having same problem installing it on Dell XPS M1530

---

### Post by jimothy on 2008-10-30
I have a very similar problem. I try to boot the 8.10 x64 live cd and i get a message saying "aperature not big enough (32mb) 64mb" .

I am guessing this is an AGP issue.

I have a acer aspire 5051 laptop, the graphic card is a ATI x1100. Oddly i tried the 8.10 beta and had no problems. I had similar problems with 8.04 so have not upgraded from 7.10 yet. I was looking forward to getting the latest system working..

Please help

---

### Post by kingofpain on 2008-10-30
Oh, seems that x64 version of the new Ubuntu has some big issues... I am unable to install it to my computer. I tried first with my ASUS CDRW. With this one, i can go to install process, but the process always interrupts with I/O error, although I tested the CD and it's ok, and I tried to install it on two different disks.
Second time, I switched the CDRW with an older ASUS CD-ROM drive, and with this one I am unable to boot into Ubuntu (same computer, different optical drive)! I get the "aperture size to small (32 instead of 64)" or somth like this and it hangs forever.](*,)

---

### Post by SkullOne on 2008-10-30
> **bishboria said:**
> I'm having identical problems.

After a while the ubuntu logo and progress bar disappear and displays buffer I/O error on device sr0...

I get the same error on both Ubuntu 8.10 64-bit and Kubuntu 8.10 64-bit.  MD5 checks out on both ISO's.  Ubuntu 64-bit 8.10 RC works fine.

Downloading x86 Ubuntu 8.10 as we speak.  Guess I'll see what happens.

I'm on a Dell Inspiron 1420.  C2D 2.2GHz, 4GB DDR2, nVidia 8400GM, with a 120GB 7200RPM Hitachi SATA drive.

---

### Post by Zorgy on 2008-10-30
8.04 and 8.10 crashes identically on my pc. 
On my dell laptop it boots fine from the cd. Haven't tried full install on the laptop.

---

### Post by ac3buddy on 2008-10-30
Yeah me too,  Upon the loading bar has stopped and the black screen went on, the message that has something to say like, Buffer I/O ,logical disk error. OMG Whats with ubuntu 8.10

---

### Post by ac3buddy on 2008-10-30
What about this? Whats the problem? me too i've tried to install in on my 64bit amd laptop and that same buffer issue error occurs.

---

### Post by Pseudo Idol on 2008-10-31
I am having similar problems.  I went to check the disk for defects and got an I/O error.  Tried to do an install anyways and got an I/O error.  It just throws an error then hangs on a black screen.

8.04 and other previous versions installed fine on this box.  Seems a bit odd to me. :confused:

This was while trying to install 64bit desktop from alternate install cd.

---

### Post by ac3buddy on 2008-10-31
Where can we get at least an immediate support for these problem?
Buffer I/O error on sr0, whats happening to ubuntu

---

### Post by ac3buddy on 2008-10-31
problem solved, i just installed the 32 bit and alas! it worked

---

### Post by bishboria on 2008-10-31
> **ac3buddy said:**
> problem solved, i just installed the 32 bit and alas! it worked

The problem I described (I/O error on device sr0) was using the 32 bit version...

I am using 8.10 now, but I had to do it the _long_ way round: install 8.04 and upgrade.

Is there something up with the release?  Has any ubuntu gurus found this problem?

bish.

---

### Post by secion8 on 2008-10-31
I am having some similar issues also with 8.10.. I can boot to the live cd(Takes a long time).. But the install does not actually install anything to my disk. it goes through and formats the drive and then the installer just hangs at 5%. I let it run about 30 minutes then the computer reboots itself back into the live cd. 

If I try to boot from HD after a supposedly succesfull install I am told there is no bootable device Press F1 to try again, F2 to run setup. 

Have tried multiple times to install but ends up writing nothing to my disk. 

Vista was installed previously but now i am left with a blank HD.

Specs:

3.0GHZ Intel Core 2 Duo
2 GB RAM 
350 GB Hard drive
Nvidia Graphics Card


Any Ideas, What is with this 8.10 release. i have installed ubuntu many times and this is first time i have had a problem like this. Acts like it cannot write to the disk.

---

### Post by Akedz on 2008-10-31
I have the same problem with the x86 disc. It does exactly the same thing that the original post describes. :(

acer travelmate
1.5 ghz intel celeron
2gb ddr2 ram

---

### Post by SkullOne on 2008-10-31
> **SkullOne said:**
> I get the same error on both Ubuntu 8.10 64-bit and Kubuntu 8.10 64-bit.  MD5 checks out on both ISO's.  Ubuntu 64-bit 8.10 RC works fine.

Downloading x86 Ubuntu 8.10 as we speak.  Guess I'll see what happens.

I'm on a Dell Inspiron 1420.  C2D 2.2GHz, 4GB DDR2, nVidia 8400GM, with a 120GB 7200RPM Hitachi SATA drive.

I get the same issue with Ubuntu x86.

I've downloaded Ubuntu x64 twice.  Ubuntu x86 once.  Kubuntu x64 once.  MD5 on all of them are correct and all give me the same buffer I/O error.

This is very annoying especially since Ubuntu x64 8.10 RC did not have this issue.

---

### Post by rampras on 2008-10-31
opened a bug, here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360)

---

### Post by SkullOne on 2008-10-31
> **rampras said:**
> opened a bug, here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360)

I updated the bug to provide more information since i386 is affected as well.  I'm at work right now so I can't try anything else.  Will try again when I get home.

---

### Post by reiki on 2008-10-31
I had this same I/O error on the first CD I burned yesterday using GnomeBaker at 4X speed. I made a new disc using Brassero at 3X speed and that one worked. This was the desktop 32-bit CD. I have not yet tried an alternate CD or the 64-bit ones. I also have an nVidia card (7300GT) in this machine and found that if I connected it using VGA instead of DVI, everything was properly detected and it even defaulted my screen resolution to 1680x1050. 

Just my experience so far.

---

### Post by tcornishmn on 2008-10-31
I'm having a similar problem - trying the x64 Alternate CD on an HP DC7600.  CD boots, but machine freezes at the very first screen where you select the language.

---

### Post by blazemore on 2008-10-31
If you're getting IO errors, or squashFS errors, it normally means your CD is dodgy. Have you tried burning at a slower speed?

Or, boot from the liveCD on a friends system, and make a liveUSB stick. It's faster booting as well!

---

### Post by SkullOne on 2008-10-31
> **reiki said:**
> I had this same I/O error on the first CD I burned yesterday using GnomeBaker at 4X speed. I made a new disc using Brassero at 3X speed and that one worked. This was the desktop 32-bit CD. I have not yet tried an alternate CD or the 64-bit ones. I also have an nVidia card (7300GT) in this machine and found that if I connected it using VGA instead of DVI, everything was properly detected and it even defaulted my screen resolution to 1680x1050. 

Just my experience so far.

I'll try cutting CD's tonight at a lower speed to see if that makes any difference.

---

### Post by mythik on 2008-10-31
I had the same problem with Sabayon Linux over a year ago, never had the problem in ubuntu 7.X or 8.04.

This forum thread seems to think they have the answer.

[http://ubuntuforums.org/showthread.php?t=886854&highlight=end_request](http://ubuntuforums.org/showthread.php?t=886854&highlight=end_request)

More specifically, 

```
Ok, I got it to work
As future reference for others who may encounter this problem, I did the following:
- Changed the drive setting in BIOS to AHCI (as opposed to IDE)
- Added following kernel boot options: acpi=off noapic udev cdroot dodmraid
```

I'm going to try the BIOS settings change first.

---

### Post by kingofpain on 2008-10-31
> **blazemore said:**
> If you're getting IO errors, or squashFS errors, it normally means your CD is dodgy. Have you tried burning at a slower speed?

Or, boot from the liveCD on a friends system, and make a liveUSB stick. It's faster booting as well!

Oh, it seems that this solved the install problem.
I burned again the iso at 4x (the lowest speed I could set) and the installation went well. 
But now i've noticed another issue: Ubuntu hangs on shutdown :lolflag:

---

### Post by SkullOne on 2008-10-31
> **kingofpain said:**
> Oh, it seems that this solved the install problem.
I burned again the iso at 4x (the lowest speed I could set) and the installation went well. 
But now i've noticed another issue: Ubuntu hangs on shutdown :lolflag:

I dunno about the shutdown problem yet but I'm in the middle of installing kubuntu 64-bit as we speak.  I burned the ISO at 24x instead of my normal 48x and all seems well.  :D

---

### Post by kingofpain on 2008-11-01
> **SkullOne said:**
> I dunno about the shutdown problem yet but I'm in the middle of installing kubuntu 64-bit as we speak.  I burned the ISO at 24x instead of my normal 48x and all seems well.  :D

It happened first time i had to reboot after install. It happened to me also when shutting down from live session.
Now I've made some updates and it seems to be ok :)

---

### Post by lomar on 2008-11-07
hey guys, i'm new at ubuntu (and linux to be honest) and i also have the very same problems with the installation of ubuntu-8.10-desktop-i386 on my laptop. 

i've tryied to do the following things:

> 
- Changed the drive setting in BIOS to AHCI (as opposed to IDE)
- Added following kernel boot options: acpi=off noapic udev cdroot dodmraid


but my bios hasn't any option for the cd-rom drive (to be more accurate, i didn't saw nowhere any "IDE", or "drive X: change connection" etc.) and when i've typed the command " acpi=off noapic udev cdroot dodmraid " next to the installation prompt, and pressed 'enter', for about 10 min (that's the maximum time i've managed to watch the... nothing :( ) nothing was happening, except from the cd-rom driver which was making the same, and the same noises again and again, like it was reading the livecd, stopped, and then again re-reading it.

the MD5 checksum of the .iso and of the burned cd-rom was ok.

if there's anything else to do, please someone suggest it to me.

i hope that you understand my horrible english, and that i've expressed myself and the problem quite clear.

ps: my laptop's configuration:

Core Duo @ 1.6 (32bit -> the iso that i've downloaded is: ubuntu-8.10-desktop-i386.iso)

1gb DDR2 @ 667Mhrz

GeForce 7600 Go - DDR2 with 256mb

wi-fi: Intel Pro/wireless 3945ABG Network Connection

the chipset -i think- its the: intel 82801G (ICH7 family).


thanks in advance :)

---

### Post by fj401971 on 2008-11-07
> **Akedz said:**
> I have the same problem with the x86 disc. It does exactly the same thing that the original post describes. :(

acer travelmate
1.5 ghz intel celeron
2gb ddr2 ram

I also have a travelmate, an Acer TravelMate 8000.  I had the same problem.

I found that "acpi=off" and "acpi=ht" allow one to boot.

But the better fix I found, was to enable "nohz=off" in the kernel module.
This so far, has solved all of my problems.

Hardware: Acer TravelMate 8000
Graphics: ATI Mobility Radeon 9700 128 MB

---

### Post by HereSkip on 2008-11-10
Can you please specify how you set the kernel options.

---

### Post by axel_2078 on 2009-02-18
Having exact same problem (buffer i/o device sr0 erros) with 32-bit version on my OEM laptop. (Intel P4 2.4 Ghz proc, 512 MB memory,). Why are so many people having problems with 8.10 Intrepid?

---

### Post by AL-X on 2009-02-18
This is about the message: 

  Buffer I/O error on device sr0

which I am getting when booting from the installation CD.

Please try this using a "Read-Only" CD or DVD reader; i.e., one that is not capable of burning (writing) to the disk.  Let us know if this helps.

---

